---
title: Ilasm.exe (Assembleur IL)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcc9ba5e379897247f50175603b1002d5688d215
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894688"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (Assembleur IL)

L'Assembleur IL génère un fichier PE (Portable Executable) en langage IL (Intermediate Language). (Pour plus d’informations sur le langage IL, consultez [Processus d’exécution managée](../../standard/managed-execution-process.md).) Vous pouvez exécuter le fichier exécutable obtenu, qui comporte le langage IL et les métadonnées nécessaires, pour déterminer si le langage IL fonctionne comme prévu.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez le texte suivant :

## <a name="syntax"></a>Syntaxe

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Paramètres

| Argument | Description |
| -------- | ----------- |
|`filename`|Nom du fichier source .il. Ce fichier est composé de directives de déclaration de métadonnées et d'instructions IL symboliques. Plusieurs arguments du fichier source peuvent être fournis pour générer un seul fichier exécutable portable avec *Ilasm.exe*. **Remarque :** vérifiez que la dernière ligne de code du fichier source .il comporte un espace blanc de fin ou un caractère de fin de ligne.|

| Option | Description |
| ------ | ----------- |
|**/32bitpreferred**|Crée une image 32 bits (PE32+).|
|**/alignment:** `integer`|Assigne à FileAlignment la valeur spécifiée par `integer` dans l'en-tête Optional NT. Lorsque la directive IL .alignment est spécifiée dans le fichier, cette option se substitue à elle.|
|**/appcontainer**|Produit un fichier *.dll* ou *.exe* qui s'exécute dans le conteneur d’application Windows comme sortie.|
|**/arm**|Spécifie l'ordinateur (ARM) Advanced RISC comme processeur cible.<br /><br /> Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/32bitpreferred**.|
|**/base:** `integer`|Assigne à ImageBase la valeur spécifiée par `integer` dans l'en-tête Optional NT. Lorsque la directive IL .imagebase est spécifiée dans le fichier, cette option se substitue à elle.|
|**/clock**|Calcule et indique la durée des compilations suivantes, en millisecondes, pour le fichier source .il :<br /><br /> **Total Run** : Durée totale d’exécution de toutes les opérations spécifiques qui suivent.<br /><br /> **Startup** : Chargement et ouverture du fichier.<br /><br /> **Emitting MD** : Envoi des métadonnées.<br /><br /> **Ref to Def Resolution** : Résolution des références aux définitions dans le fichier.<br /><br /> **CEE File Generation** : Génération de l’image du fichier en mémoire.<br /><br /> **Écriture du fichier PE** : Écriture de l’image dans un fichier PE.|
|**/debug**[:**IMPL**&#124;**OPT**]|Inclut des informations de débogage (noms des variables locales et des arguments et numéros de ligne). Crée un fichier PDB.<br /><br /> **/debug** sans valeur supplémentaire désactive l'optimisation JIT et utilise des points de séquence du fichier PDB.<br /><br /> **IMPL** désactive l'optimisation JIT et utilise des points de séquence implicites.<br /><br /> **OPT** active l'optimisation JIT et utilise des points de séquence implicites.|
|**/dll**|Génère un fichier *.dll* en tant que sortie.|
|**/enc:** `file`|Crée des deltas Modifier && Continuer à partir du fichier source spécifié.<br /><br /> Cet argument est utilisé uniquement à titre d'information et n'est pas pris en charge pour une utilisation commerciale.|
|**/exe**|Génère un fichier exécutable en tant que sortie. Il s'agit de la valeur par défaut.|
|**/flags:** `integer`|Assigne à ImageFlags la valeur spécifiée par `integer` dans l'en-tête du Common Language Runtime. Lorsque la directive IL .corflags est spécifiée dans le fichier, cette option se substitue à elle. Consultez CorHdr.h , COMIMAGE_FLAGS pour obtenir la liste des valeurs valides pour *integer*.|
|**/fold**|Insère des corps de méthode identiques en un seul.|
|/ **/highentropyva**|Produit un fichier exécutable de sortie qui prend en charge l'Address Space Layout Randomization (ASLR) de forte entropie. (Par défaut pour **/appcontainer**)|
|**/include:** `includePath`|Définit un chemin d'accès pour rechercher des fichiers fournis avec `#include`.|
|**/itanium**|Spécifie Intel Itanium comme processeur cible.<br /><br /> Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/pe64**.|
|**/key:** `keyFile`|Compile `filename` avec une signature forte à l’aide de la clé privée figurant dans `keyFile`.|
|**/key:**  @`keySource`|Compile `filename` avec une signature forte à l’aide de la clé privée produite dans `keySource`.|
|**/listing**|Génère un fichier listing lors de la sortie standard. Si vous omettez cette option, aucun fichier listing n'est alors généré.<br /><br /> Ce paramètre n'est pas pris en charge dans les versions 2.0 et ultérieures du .NET Framework.|
|**/mdv:** `versionString`|Définit la chaîne de version de métadonnées.|
|**/msv:** `major`.`minor`|Définit la version de flux de métadonnées, dans laquelle `major` et `minor` sont des entiers.|
|**/noautoinherit**|Désactive l'héritage par défaut de <xref:System.Object> lorsque aucune classe de base n'est spécifiée.|
|**/nocorstub**|Supprime la génération du stub CORExeMain.|
|**/nologo**|Supprime l'affichage de la bannière de démarrage Microsoft.|
|**/output:** `file.ext`|Spécifie le nom du fichier de sortie et son extension. Le nom du fichier de sortie est, par défaut, le même que le nom du premier fichier source. L’extension par défaut est *.exe*. Si vous spécifiez l'option **/dll**, l'extension par défaut est *.dll*. **Remarque :** La spécification de **/output**:myfile.dll ne définit pas l’option **/dll**. Si vous ne spécifiez pas l’option **/dll**, il en résultera un fichier exécutable nommé *myfile.dll*.|
|**/optimize**|Optimise les instructions allongées en instructions abrégées. Par exemple, `br` en `br.s`.|
|**/pe64**|Crée une image 64 bits (PE32+).<br /><br /> Si aucun processeur cible n'est spécifié, la valeur par défaut est `/itanium`.|
|**/pdb**|Crée un fichier PDB sans activer le suivi des informations de débogage.|
|**/quiet**|Spécifie le mode silencieux ; ne fait pas état de la progression de l'assembly.|
|**/resource:** `file.res`|Inclut le fichier de ressources spécifié au format \*.res dans le fichier *.exe* ou *.dll* obtenu. Un seul fichier .res peut être spécifié avec l'option **/resource** .|
|**/ssver:** `int`.`int`|Définit le numéro de version du sous-système dans l'en-tête Optional NT. Pour **/appcontainer** et **/arm** le numéro de version minimale est 6.02.|
|**/stack:** `stackSize`|Affecte `stackSize`à la valeur SizeOfStackReserve dans l'en-tête Optional NT.|
|**/stripreloc**|Spécifie qu'aucun réadressage de base n'est requis.|
|**/subsystem:** `integer`|Assigne à subsystem la valeur spécifiée par `integer` dans l’en-tête Optional NT. Lorsque la directive IL .subsystem est spécifiée dans le fichier, cette option se substitue à elle. Consultez winnt.h, IMAGE_SUBSYSTEM pour obtenir la liste des valeurs valides pour `integer`.|
|**/x64**|Spécifie un processeur AMD 64 bits comme processeur cible.<br /><br /> Si aucune largeur de bits d'image n'est spécifiée, la valeur par défaut est **/pe64**.|
|**/?**|Affiche la syntaxe et les options de commande de l'outil.|

> [!NOTE]
> Aucune option d’*Ilasm.exe* ne respecte la casse et toutes se reconnaissent à leurs trois premières lettres. Par exemple, **/lis** équivaut à **/listing** et **/res:** myresfile.res équivaut à **/resource:** myresfile.res. Les options spécifiant des arguments prennent en charge les deux-points (:) ou le signe égal (=) en tant que séparateur entre l'option et l'argument. Par exemple, **/output**:*file.ext* équivaut à **/output**=*file.ext*.

## <a name="remarks"></a>Notes

L'Assembleur IL permet aux fournisseurs d'outils de concevoir et d'implémenter des générateurs IL. Avec *Ilasm.exe*, les développeurs d’outils et de compilateurs peuvent se concentrer sur le langage IL et la génération de métadonnées sans se préoccuper de l’émission du langage IL au format de fichier exécutable portable.

Comparable à d'autres compilateurs ayant pour cible le runtime, tels que C# et Visual Basic, *Ilasm.exe* ne génère pas de fichiers objets intermédiaires et ne nécessite pas d’étape de liaison pour constituer un fichier exécutable portable.

L'Assembleur IL peut exprimer toutes les fonctionnalités métadonnées et IL existantes des langages de programmation ayant pour cible le runtime. Du code managé écrit dans l’un de ces langages de programmation peut ainsi être correctement exprimé dans l’Assembleur IL et compilé avec *Ilasm.exe*.

> [!NOTE]
> La compilation peut échouer si la dernière ligne de code du fichier source .il ne comporte pas d'espace blanc de fin ou de caractère de fin de ligne.

Vous pouvez utiliser *Ilasm.exe* avec l’outil qui lui est associé, [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* utilise un fichier PE qui contient le code IL et crée un fichier texte qu’il peut utiliser en entrée dans *Ilasm.exe*. Cet outil s'avère, par exemple, utile lors de la compilation d'un code dans un langage de programmation ne prenant pas en charge tous les attributs de métadonnées du runtime. Une fois le code compilé et la sortie exécutée via *Ildasm.exe*, le fichier texte IL obtenu peut être modifié manuellement pour y ajouter les attributs manquants. Vous pouvez ensuite exécuter ce fichier texte via *Ilasm.exe* pour générer un fichier exécutable final.

Vous pouvez également utiliser cette technique pour générer un seul fichier exécutable portable à partir de plusieurs fichiers exécutables portables provenant de différents compilateurs.

> [!NOTE]
> Actuellement, vous ne pouvez pas utiliser cette technique avec des fichiers exécutables portables qui contiennent du code natif incorporé (par exemple, des fichiers exécutables portables générés par Visual C++).

Pour que cette utilisation conjointe d’*Ildasm.exe* et d’*Ilasm.exe* soit la plus exacte possible, l’assembleur ne substitue pas par défaut les encodages abrégés par un codage allongé que vous avez pu écrire dans vos sources IL (ou qu’un autre compilateur a pu émettre). Utilisez l'option **/optimize** pour remplacer les encodages abrégés dans la mesure du possible.

> [!NOTE]
> *Ildasm.exe* ne fonctionne qu’avec des fichiers stockés sur le disque. Il ne fonctionne pas avec des fichiers installés dans le Global Assembly Cache.

Pour plus d’informations sur la grammaire du langage IL, consultez le fichier asmparse.grammar dans le SDK Windows.

## <a name="version-information"></a>Informations sur la version

À compter de .NET Framework 4.5, joignez un attribut personnalisé à une implémentation d’interface à l’aide d’un code semblable au suivant :

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

À compter de .NET Framework 4.5, spécifiez un objet blob (Binary Large Object) marshal arbitraire à l’aide de sa représentation binaire brute, comme indiqué dans le code suivant :

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Pour plus d’informations sur la grammaire du langage IL, consultez le fichier asmparse.grammar dans le SDK Windows.

## <a name="examples"></a>Exemples

La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier exécutable *myTestFile.exe*.

```console
ilasm myTestFile
```

La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier *.dll*, *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

La commande suivante assemble le fichier IL *myTestFile.il* et génère le fichier *.dll*, *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

L’exemple de code suivant illustre une application extrêmement simple qui affiche « Hello World! » dans la console. Vous pouvez compiler ce code, puis utiliser l’outil [*Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour générer un fichier IL.

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

L'exemple de code IL suivant correspond à l'exemple de code C# précédent. Vous pouvez compiler ce code dans un assembly à l’aide de l’Assembleur IL. Les exemples de code IL et C# affichent « Hello World! » dans la console.

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a>Voir aussi

- [Outils](../../../docs/framework/tools/index.md)
- [*Ildasm.exe* (Désassembleur IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [Processus d'exécution managée](../../standard/managed-execution-process.md)
- [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
