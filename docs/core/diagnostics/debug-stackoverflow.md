---
title: Débogage des erreurs StackOverflow
description: Découvrez comment diagnostiquer les exceptions StackOverflow
ms.topic: tutorial
ms.date: 12/22/2020
ms.openlocfilehash: 92edf854ddcc2e778949d74eff1370cf27db25b4
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97764927"
---
# <a name="debugging-stackoverflow-errors"></a>Débogage des erreurs StackOverflow

Une <xref:System.StackOverflowException> exception est levée lorsque la capacité de la pile d’exécution est dépassée, car elle contient un trop grand nombre d’appels de méthode imbriqués.  

Supposons, par exemple, que vous ayez une application comme suit :

````
using System;

namespace temp
{
    class Program
    {
        static void Main(string[] args)
        {
            Main(args); // oops this recursion won't stop
        }
    }
}
````

La méthode main se appellera continuellement jusqu’à ce qu’il n’y ait plus d’espace de pile.  Une fois qu’il n’y a plus d’espace de pile, l’exécution ne peut pas se poursuivre et lève donc un <xref:System.StackOverflowException> .  

````
> dotnet run
Stack overflow.
````

> [!NOTE]
> Sur .NET 5 et versions ultérieures, la pile des appels est sortie vers la console.

> [!NOTE]
> Cet article explique comment déboguer un dépassement de capacité de la pile avec lldb. Si vous exécutez sur Windows, nous vous suggérons de déboguer l’application avec [Visual Studio](/visualstudio/debugger/what-is-debugging) ou [Visual Studio code](https://code.visualstudio.com/Docs/editor/debugging).  

## <a name="example"></a>Exemple

1. Exécuter l’application avec celle-ci configurée pour collecter un vidage en cas d’incident

    ````
    > export COMPlus_DbgEnableMiniDump=1
    > dotnet run
    Stack overflow.
    Writing minidump with heap to file /tmp/coredump.6412
    Written 58191872 bytes (14207 pages) to core file
    ````

2. Installer l’extension SOS à l’aide [de dotnet-SOS](dotnet-sos.md)

    ````
    dotnet-sos install
    ````

3. Déboguer le dump dans lldb pour voir la pile défectueuse

    ````
    lldb --core /temp/coredump.6412
    (lldb) bt
    ...
        frame #261930: 0x00007f59b40900cc
        frame #261931: 0x00007f59b40900cc
        frame #261932: 0x00007f59b40900cc
        frame #261933: 0x00007f59b40900cc
        frame #261934: 0x00007f59b40900cc
        frame #261935: 0x00007f5a2d4a080f libcoreclr.so`CallDescrWorkerInternal at unixasmmacrosamd64.inc:867
        frame #261936: 0x00007f5a2d3cc4c3 libcoreclr.so`MethodDescCallSite::CallTargetWorker(unsigned long const*, unsigned long*, int) at callhelpers.cpp:70
        frame #261937: 0x00007f5a2d3cc468 libcoreclr.so`MethodDescCallSite::CallTargetWorker(this=<unavailable>, pArguments=0x00007ffe8222e7b0, pReturnValue=0x0000000000000000, cbReturnValue=0) at callhelpers.cpp:604
        frame #261938: 0x00007f5a2d4b6182 libcoreclr.so`RunMain(MethodDesc*, short, int*, PtrArray**) [inlined] MethodDescCallSite::Call(this=<unavailable>, pArguments=<unavailable>) at callhelpers.h:468
    ...
    ````

4. Le frame supérieur `0x00007f59b40900cc` est répété plusieurs fois. Utilisez la commande [SOS](sos-debugging-extension.md) `ip2md` pour déterminer la méthode qui se trouve à l' `0x00007f59b40900cc` adresse

    ````
    (lldb) ip2md 0x00007f59b40900cc
    MethodDesc:   00007f59b413ffa8
    Method Name:          temp.Program.Main(System.String[])
    Class:                00007f59b4181d40
    MethodTable:          00007f59b4190020
    mdToken:              0000000006000001
    Module:               00007f59b413dbf8
    IsJitted:             yes
    Current CodeAddr:     00007f59b40900a0
    Version History:
      ILCodeVersion:      0000000000000000
      ReJIT ID:           0
      IL Addr:            0000000000000000
         CodeAddr:           00007f59b40900a0  (MinOptJitted)
         NativeCodeVersion:  0000000000000000
    Source file:  /temp/Program.cs @ 9
    ````

5. Accédez à la méthode spécifiée Temp. Program. main (System. String []) et source « /temp/Program.cs @ 9 » pour voir si vous pouvez déterminer ce que vous avez fait. S’il n’est toujours pas clair, vous pouvez ajouter la journalisation dans cette zone du code.

## <a name="see-also"></a>Voir aussi

* [Introduction aux dumps dans .NET](dumps.md)
* [Déboguer des vidages Linux](debug-linux-dumps.md)
* [Extension de débogage SOS pour .NET](sos-debugging-extension.md)
