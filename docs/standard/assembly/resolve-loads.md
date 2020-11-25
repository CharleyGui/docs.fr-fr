---
title: Résoudre les chargements d’assembly
description: Cet article décrit l’événement .NET AppDomain. AssemblyResolve. Utilisez cet événement pour les applications qui requièrent le contrôle du chargement d’assembly.
ms.date: 08/20/2019
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
ms.openlocfilehash: edd101e57793668d71d44db08f191ae412c6d998
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720904"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="8b803-104">Résoudre les chargements d’assembly</span><span class="sxs-lookup"><span data-stu-id="8b803-104">Resolve assembly loads</span></span>

<span data-ttu-id="8b803-105">.NET fournit l' <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> événement pour les applications qui requièrent un plus grand contrôle sur le chargement de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8b803-105">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="8b803-106">En gérant cet événement, votre application peut charger un assembly dans le contexte de chargement à l’extérieur des chemins de détection normaux, sélectionner la version d’assembly à charger parmi plusieurs, émettre un assembly dynamique et le retourner, etc.</span><span class="sxs-lookup"><span data-stu-id="8b803-106">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="8b803-107">Cette rubrique fournit des instructions sur la gestion de l’événement <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="8b803-107">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b803-108">Pour résoudre les chargements d’assemblys dans le contexte ReflectionOnly, utilisez l’événement <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> à la place.</span><span class="sxs-lookup"><span data-stu-id="8b803-108">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="8b803-109">Fonctionnement de l’événement AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="8b803-109">How the AssemblyResolve event works</span></span>  

 <span data-ttu-id="8b803-110">Quand vous inscrivez un gestionnaire pour l’événement <xref:System.AppDomain.AssemblyResolve>, le gestionnaire est appelé chaque fois que le runtime ne peut pas établir de liaison à un assembly par nom.</span><span class="sxs-lookup"><span data-stu-id="8b803-110">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="8b803-111">Par exemple, l’appel des méthodes suivantes à partir du code utilisateur peut provoquer le déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve> :</span><span class="sxs-lookup"><span data-stu-id="8b803-111">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="8b803-112">surcharge de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dont le premier argument est une chaîne qui représente le nom complet de l’assembly à charger (autrement dit, la chaîne retournée par la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>) ;</span><span class="sxs-lookup"><span data-stu-id="8b803-112">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="8b803-113">surcharge de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dont le premier argument est un objet <xref:System.Reflection.AssemblyName> qui identifie l’assembly à charger ;</span><span class="sxs-lookup"><span data-stu-id="8b803-113">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="8b803-114">surcharge de méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> ;</span><span class="sxs-lookup"><span data-stu-id="8b803-114">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="8b803-115">surcharge de méthode <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> qui instancie un objet dans un autre domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8b803-115">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="8b803-116">Ce que fait le gestionnaire d’événements</span><span class="sxs-lookup"><span data-stu-id="8b803-116">What the event handler does</span></span>  

 <span data-ttu-id="8b803-117">Le gestionnaire de l’événement <xref:System.AppDomain.AssemblyResolve> reçoit le nom complet de l’assembly à charger dans la propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b803-117">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8b803-118">Si le gestionnaire ne reconnaît pas le nom de l’assembly, il retourne `null` (C#), `Nothing` (Visual Basic) ou `nullptr` (Visual C++).</span><span class="sxs-lookup"><span data-stu-id="8b803-118">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="8b803-119">Si le gestionnaire reconnaît le nom de l’assembly, il peut charger et retourner un assembly qui satisfait la requête.</span><span class="sxs-lookup"><span data-stu-id="8b803-119">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="8b803-120">La liste suivante décrit des exemples de scénarios.</span><span class="sxs-lookup"><span data-stu-id="8b803-120">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="8b803-121">Si le gestionnaire connaît l’emplacement d’une version de l’assembly, il peut charger l’assembly à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>, et retourner l’assembly chargé si l’opération réussit.</span><span class="sxs-lookup"><span data-stu-id="8b803-121">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="8b803-122">Si le gestionnaire a accès à une base de données d’assemblys stockés sous la forme de tableaux d’octets, il peut charger un tableau d’octets à l’aide de l’une des surcharges de méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> qui acceptent un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="8b803-122">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="8b803-123">Le gestionnaire peut générer un assembly dynamique et le retourner.</span><span class="sxs-lookup"><span data-stu-id="8b803-123">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b803-124">Le gestionnaire doit charger l’assembly dans le contexte LoadFrom, dans le contexte de chargement ou sans contexte. Si le gestionnaire charge l’assembly dans le contexte ReflectionOnly à l’aide de la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, la tentative de chargement ayant déclenché l’événement <xref:System.AppDomain.AssemblyResolve> échoue.</span><span class="sxs-lookup"><span data-stu-id="8b803-124">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="8b803-125">Il appartient au gestionnaire d’événements de retourner un assembly approprié.</span><span class="sxs-lookup"><span data-stu-id="8b803-125">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="8b803-126">Le gestionnaire peut analyser le nom complet de l’assembly demandé en passant la valeur de propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> au constructeur <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="8b803-126">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="8b803-127">À compter de .NET Framework 4, le gestionnaire peut utiliser la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> pour déterminer si la requête actuelle est une dépendance d’un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="8b803-127">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="8b803-128">Ces informations permettent d’identifier un assembly qui satisfait la dépendance.</span><span class="sxs-lookup"><span data-stu-id="8b803-128">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="8b803-129">Le gestionnaire d’événements peut retourner une version de l’assembly différente de celle qui a été demandée.</span><span class="sxs-lookup"><span data-stu-id="8b803-129">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="8b803-130">Dans la plupart des cas, l’assembly qui est retourné par le gestionnaire apparaît dans le contexte de chargement, indépendamment du contexte dans lequel le gestionnaire le charge.</span><span class="sxs-lookup"><span data-stu-id="8b803-130">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="8b803-131">Par exemple, si le gestionnaire utilise la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> pour charger un assembly dans le contexte LoadFrom, l’assembly apparaît dans le contexte de chargement quand le gestionnaire le retourne.</span><span class="sxs-lookup"><span data-stu-id="8b803-131">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="8b803-132">Toutefois, dans le cas suivant, l’assembly apparaît sans contexte quand le gestionnaire le retourne :</span><span class="sxs-lookup"><span data-stu-id="8b803-132">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="8b803-133">le gestionnaire charge un assembly sans contexte ;</span><span class="sxs-lookup"><span data-stu-id="8b803-133">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="8b803-134">la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> n’a pas la valeur Null ;</span><span class="sxs-lookup"><span data-stu-id="8b803-134">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="8b803-135">l’assembly demandeur (c’est-à-dire, l’assembly retourné par la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) a été chargé sans contexte.</span><span class="sxs-lookup"><span data-stu-id="8b803-135">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="8b803-136">Pour plus d’informations sur les contextes, consultez la surcharge de méthode <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b803-136">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="8b803-137">Vous pouvez charger plusieurs versions du même assembly dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8b803-137">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="8b803-138">Cette pratique n’est pas recommandée, car elle peut entraîner des problèmes d’assignation de type.</span><span class="sxs-lookup"><span data-stu-id="8b803-138">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="8b803-139">Consultez [meilleures pratiques pour le chargement d’assembly](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="8b803-139">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="8b803-140">Ce que le gestionnaire d’événements ne doit pas faire</span><span class="sxs-lookup"><span data-stu-id="8b803-140">What the event handler should not do</span></span>  

<span data-ttu-id="8b803-141">La règle principale pour gérer l’événement <xref:System.AppDomain.AssemblyResolve> est que vous ne devez pas essayer de retourner un assembly que vous ne reconnaissez pas.</span><span class="sxs-lookup"><span data-stu-id="8b803-141">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="8b803-142">Quand vous écrivez le gestionnaire, vous devez avoir connaissance des assemblys qui peuvent provoquer le déclenchement de l’événement.</span><span class="sxs-lookup"><span data-stu-id="8b803-142">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="8b803-143">Votre gestionnaire doit retourner Null pour d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="8b803-143">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="8b803-144">À compter de .NET Framework 4, l’événement <xref:System.AppDomain.AssemblyResolve> est déclenché pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="8b803-144">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="8b803-145">Ce changement affecte un gestionnaire d’événements qui a été écrit pour une version antérieure du .NET Framework, si le gestionnaire tente de résoudre toutes les requêtes de chargement d’assembly.</span><span class="sxs-lookup"><span data-stu-id="8b803-145">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="8b803-146">Les gestionnaires d’événements qui ignorent les assemblys non reconnus ne sont pas affectés par ce changement : ils retournent la valeur Null et les mécanismes de secours normaux sont suivis.</span><span class="sxs-lookup"><span data-stu-id="8b803-146">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="8b803-147">Durant le chargement d’un assembly, le gestionnaire d’événements ne doit pas utiliser les surcharges de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> qui peuvent provoquer le déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve> de manière récursive, car cela peut provoquer un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="8b803-147">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="8b803-148">(Consultez la liste fournie plus haut dans cette rubrique.) Cela se produit même si vous fournissez une gestion des exceptions pour la demande de chargement, car aucune exception n’est levée tant que tous les gestionnaires d’événements n’ont pas été retournés.</span><span class="sxs-lookup"><span data-stu-id="8b803-148">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="8b803-149">Le code suivant provoque donc un dépassement de capacité de la pile si `MyAssembly` est introuvable :</span><span class="sxs-lookup"><span data-stu-id="8b803-149">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

```cpp
using namespace System;
using namespace System::Reflection;

ref class Example
{
internal:
    static Assembly^ MyHandler(Object^ source, ResolveEventArgs^ e)
    {
        Console::WriteLine("Resolving {0}", e->Name);
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

## <a name="see-also"></a><span data-ttu-id="8b803-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b803-150">See also</span></span>

- [<span data-ttu-id="8b803-151">Meilleures pratiques pour le chargement d’assembly</span><span class="sxs-lookup"><span data-stu-id="8b803-151">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="8b803-152">Utiliser des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="8b803-152">Use application domains</span></span>](../../framework/app-domains/use.md)
