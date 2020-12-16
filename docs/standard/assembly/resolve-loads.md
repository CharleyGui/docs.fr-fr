---
title: Résoudre les chargements d’assembly
description: Cet article décrit l’événement .NET AppDomain. AssemblyResolve. Utilisez cet événement pour les applications qui requièrent le contrôle du chargement d’assembly.
ms.date: 12/15/2020
helpviewer_keywords:
- assemblies [.NET], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 63545db31a4290ce933da45c0957dfdb2a00701c
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593862"
---
# <a name="resolve-assembly-loads"></a>Résoudre les chargements d’assembly

.NET fournit l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement pour les applications qui requièrent un plus grand contrôle sur le chargement de l’assembly. En gérant cet événement, votre application peut charger un assembly dans le contexte de chargement à l’extérieur des chemins de détection normaux, sélectionner la version d’assembly à charger parmi plusieurs, émettre un assembly dynamique et le retourner, etc. Cette rubrique fournit des instructions sur la gestion de l’événement <xref:System.AppDomain.AssemblyResolve>.

> [!NOTE]
> Pour résoudre les chargements d’assemblys dans le contexte ReflectionOnly, utilisez l’événement <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> à la place.

## <a name="how-the-assemblyresolve-event-works"></a>Fonctionnement de l’événement AssemblyResolve

Quand vous inscrivez un gestionnaire pour l’événement <xref:System.AppDomain.AssemblyResolve>, le gestionnaire est appelé chaque fois que le runtime ne peut pas établir de liaison à un assembly par nom. Par exemple, l’appel des méthodes suivantes à partir du code utilisateur peut provoquer le déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve> :

- surcharge de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dont le premier argument est une chaîne qui représente le nom complet de l’assembly à charger (autrement dit, la chaîne retournée par la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>) ;

- surcharge de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dont le premier argument est un objet <xref:System.Reflection.AssemblyName> qui identifie l’assembly à charger ;

- surcharge de méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> ;

- surcharge de méthode <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> qui instancie un objet dans un autre domaine d’application.

## <a name="what-the-event-handler-does"></a>Ce que fait le gestionnaire d’événements

Le gestionnaire de l’événement <xref:System.AppDomain.AssemblyResolve> reçoit le nom complet de l’assembly à charger dans la propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>. Si le gestionnaire ne reconnaît pas le nom de l’assembly, il retourne `null` (C#), `Nothing` (Visual Basic) ou `nullptr` (Visual C++).

Si le gestionnaire reconnaît le nom de l’assembly, il peut charger et retourner un assembly qui satisfait la requête. La liste suivante décrit des exemples de scénarios.

- Si le gestionnaire connaît l’emplacement d’une version de l’assembly, il peut charger l’assembly à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>, et retourner l’assembly chargé si l’opération réussit.

- Si le gestionnaire a accès à une base de données d’assemblys stockés sous la forme de tableaux d’octets, il peut charger un tableau d’octets à l’aide de l’une des surcharges de méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> qui acceptent un tableau d’octets.

- Le gestionnaire peut générer un assembly dynamique et le retourner.

> [!NOTE]
> Le gestionnaire doit charger l’assembly dans le contexte de chargement, dans le contexte de chargement ou sans contexte. Si le gestionnaire charge l’assembly dans le contexte de réflexion uniquement à l’aide de la <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> méthode ou, la tentative de chargement qui a déclenché l' <xref:System.AppDomain.AssemblyResolve> événement échoue.

Il appartient au gestionnaire d’événements de retourner un assembly approprié. Le gestionnaire peut analyser le nom complet de l’assembly demandé en passant la valeur de propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> au constructeur <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>. À compter de .NET Framework 4, le gestionnaire peut utiliser la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> pour déterminer si la requête actuelle est une dépendance d’un autre assembly. Ces informations permettent d’identifier un assembly qui satisfait la dépendance.

Le gestionnaire d’événements peut retourner une version de l’assembly différente de celle qui a été demandée.

Dans la plupart des cas, l’assembly qui est retourné par le gestionnaire apparaît dans le contexte de chargement, indépendamment du contexte dans lequel le gestionnaire le charge. Par exemple, si le gestionnaire utilise la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> pour charger un assembly dans le contexte LoadFrom, l’assembly apparaît dans le contexte de chargement quand le gestionnaire le retourne. Toutefois, dans le cas suivant, l’assembly apparaît sans contexte quand le gestionnaire le retourne :

- le gestionnaire charge un assembly sans contexte ;

- la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> n’a pas la valeur Null ;

- l’assembly demandeur (c’est-à-dire, l’assembly retourné par la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) a été chargé sans contexte.

Pour plus d’informations sur les contextes, consultez la surcharge de méthode <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.

Vous pouvez charger plusieurs versions du même assembly dans le même domaine d’application. Cette pratique n’est pas recommandée, car elle peut entraîner des problèmes d’assignation de type. Consultez [meilleures pratiques pour le chargement d’assembly](../../framework/deployment/best-practices-for-assembly-loading.md).

## <a name="what-the-event-handler-should-not-do"></a>Ce que le gestionnaire d’événements ne doit pas faire

La règle principale pour gérer l’événement <xref:System.AppDomain.AssemblyResolve> est que vous ne devez pas essayer de retourner un assembly que vous ne reconnaissez pas. Quand vous écrivez le gestionnaire, vous devez avoir connaissance des assemblys qui peuvent provoquer le déclenchement de l’événement. Votre gestionnaire doit retourner Null pour d’autres assemblys.

> [!IMPORTANT]
> À compter de .NET Framework 4, l’événement <xref:System.AppDomain.AssemblyResolve> est déclenché pour les assemblys satellites. Ce changement affecte un gestionnaire d’événements qui a été écrit pour une version antérieure du .NET Framework, si le gestionnaire tente de résoudre toutes les requêtes de chargement d’assembly. Les gestionnaires d’événements qui ignorent les assemblys qu’ils ne reconnaissent pas ne sont pas affectés par cette modification : ils retournent `null` et les mécanismes de secours normaux sont suivis.

Durant le chargement d’un assembly, le gestionnaire d’événements ne doit pas utiliser les surcharges de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> qui peuvent provoquer le déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve> de manière récursive, car cela peut provoquer un dépassement de capacité de la pile. (Consultez la liste fournie plus haut dans cette rubrique.) Cela se produit même si vous fournissez une gestion des exceptions pour la demande de chargement, car aucune exception n’est levée tant que tous les gestionnaires d’événements n’ont pas été retournés. Le code suivant provoque donc un dépassement de capacité de la pile si `MyAssembly` est introuvable :

```csharp
using System;
using System.Reflection;

class BadExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);
        // DO NOT DO THIS: This causes a StackOverflowException
        return Assembly.Load(e.Name);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
 */
```

```vb
Imports System.Reflection

Class BadExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object, _
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)
        // DO NOT DO THIS: This causes a StackOverflowException
        Return Assembly.Load(e.Name)
    End Function
End Class

' This example produces output similar to the following:
'
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'...
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
'
'Process is terminated due to StackOverflowException.
```

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
        // DO NOT DO THIS: This causes a StackOverflowException
        return Assembly::Load(e->Name);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}

/* This example produces output similar to the following:

Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
...
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null
Resolving MyAssembly, Version=1.2.3.4, Culture=neutral, PublicKeyToken=null

Process is terminated due to StackOverflowException.
*/
```

### <a name="the-correct-way-to-handle-assemblyresolve"></a>La méthode correcte pour gérer AssemblyResolve

Lors de la résolution d’assemblys à partir du <xref:System.AppDomain.AssemblyResolve> Gestionnaire d’événements, une <xref:System.StackOverflowException> est finalement levée si le gestionnaire utilise les appels de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> méthode ou. Utilisez plutôt <xref:System.Reflection.Assembly.LoadFile%2A> <xref:System.Reflection.Assembly.LoadFrom%2A> les méthodes ou, car elles ne déclenchent pas l' `AssemblyResolve` événement.

Imaginez que `MyAssembly.dll` se trouve près de l’assembly en cours d’exécution, dans un emplacement connu, il peut être résolu à l’aide `Assembly.LoadFile` du chemin d’accès à l’assembly donné.

```csharp
using System;
using System.IO;
using System.Reflection;

class CorrectExample
{
    static void Main()
    {
        AppDomain ad = AppDomain.CreateDomain("Test");
        ad.AssemblyResolve += MyHandler;

        try
        {
            object obj = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType");
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    static Assembly MyHandler(object source, ResolveEventArgs e)
    {
        Console.WriteLine("Resolving {0}", e.Name);

        var path = Path.GetFullPath("../../MyAssembly.dll");
        return Assembly.LoadFile(path);
     }
}
```

```vb
Imports System.IO
Imports System.Reflection

Class CorrectExample

    Shared Sub Main()

        Dim ad As AppDomain = AppDomain.CreateDomain("Test")
        AddHandler ad.AssemblyResolve, AddressOf MyHandler

        Try
            Dim obj As Object = ad.CreateInstanceAndUnwrap(
                "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
                "MyType")
        Catch ex As Exception
            Console.WriteLine(ex.Message)
        End Try
    End Sub

    Shared Function MyHandler(ByVal source As Object,
                              ByVal e As ResolveEventArgs) As Assembly
        Console.WriteLine("Resolving {0}", e.Name)

        Dim fullPath = Path.GetFullPath("../../MyAssembly.dll")
        Return Assembly.LoadFile(fullPath)
    End Function
End Class
```

```cpp
using namespace System;
using namespace System::IO;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);

        String^ fullPath = Path::GetFullPath("../../MyAssembly.dll");
        return Assembly::LoadFile(fullPath);
    }
};

void main()
{
    AppDomain^ ad = AppDomain::CreateDomain("Test");
    ad->AssemblyResolve += gcnew ResolveEventHandler(&Example::MyHandler);

    try
    {
        Object^ obj = ad->CreateInstanceAndUnwrap(
            "MyAssembly, version=1.2.3.4, culture=neutral, publicKeyToken=null",
            "MyType");
    }
    catch (Exception^ ex)
    {
        Console::WriteLine(ex->Message);
    }
}
```

## <a name="see-also"></a>Voir aussi

- [Meilleures pratiques pour le chargement d’assembly](../../framework/deployment/best-practices-for-assembly-loading.md)
- [Utiliser des domaines d’application](../../framework/app-domains/use.md)
