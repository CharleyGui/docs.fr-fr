---
title: Résoudre les chargements d’assembly
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d6314fae266505fbb4410aaaa351973070ab3811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156437"
---
# <a name="resolve-assembly-loads"></a><span data-ttu-id="30142-102">Résoudre les chargements d’assembly</span><span class="sxs-lookup"><span data-stu-id="30142-102">Resolve assembly loads</span></span>
<span data-ttu-id="30142-103">.NET fournit <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement pour les applications qui nécessitent un plus grand contrôle sur le chargement de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="30142-103">.NET provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="30142-104">En gérant cet événement, votre application peut charger un assembly dans le contexte de chargement à l’extérieur des chemins de détection normaux, sélectionner la version d’assembly à charger parmi plusieurs, émettre un assembly dynamique et le retourner, etc.</span><span class="sxs-lookup"><span data-stu-id="30142-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="30142-105">Cette rubrique fournit des instructions sur la gestion de l’événement <xref:System.AppDomain.AssemblyResolve>.</span><span class="sxs-lookup"><span data-stu-id="30142-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30142-106">Pour résoudre les chargements d’assemblys dans le contexte ReflectionOnly, utilisez l’événement <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> à la place.</span><span class="sxs-lookup"><span data-stu-id="30142-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="30142-107">Fonctionnement de l’événement AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="30142-107">How the AssemblyResolve event works</span></span>  
 <span data-ttu-id="30142-108">Quand vous inscrivez un gestionnaire pour l’événement <xref:System.AppDomain.AssemblyResolve>, le gestionnaire est appelé chaque fois que le runtime ne peut pas établir de liaison à un assembly par nom.</span><span class="sxs-lookup"><span data-stu-id="30142-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="30142-109">Par exemple, l’appel des méthodes suivantes à partir du code utilisateur peut provoquer le déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve> :</span><span class="sxs-lookup"><span data-stu-id="30142-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
- <span data-ttu-id="30142-110">surcharge de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dont le premier argument est une chaîne qui représente le nom complet de l’assembly à charger (autrement dit, la chaîne retournée par la propriété <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>) ;</span><span class="sxs-lookup"><span data-stu-id="30142-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
- <span data-ttu-id="30142-111">surcharge de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> dont le premier argument est un objet <xref:System.Reflection.AssemblyName> qui identifie l’assembly à charger ;</span><span class="sxs-lookup"><span data-stu-id="30142-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
- <span data-ttu-id="30142-112">surcharge de méthode <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> ;</span><span class="sxs-lookup"><span data-stu-id="30142-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
- <span data-ttu-id="30142-113">surcharge de méthode <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> ou <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> qui instancie un objet dans un autre domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30142-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="30142-114">Ce que fait le gestionnaire d’événements</span><span class="sxs-lookup"><span data-stu-id="30142-114">What the event handler does</span></span>  
 <span data-ttu-id="30142-115">Le gestionnaire de l’événement <xref:System.AppDomain.AssemblyResolve> reçoit le nom complet de l’assembly à charger dans la propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30142-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="30142-116">Si le gestionnaire ne reconnaît pas `null` le nom `Nothing` de l’assemblage, il revient (C), (Visual Basic) ou `nullptr` (Visual CMD).</span><span class="sxs-lookup"><span data-stu-id="30142-116">If the handler does not recognize the assembly name, it returns `null` (C#), `Nothing` (Visual Basic), or `nullptr` (Visual C++).</span></span>  
  
 <span data-ttu-id="30142-117">Si le gestionnaire reconnaît le nom de l’assembly, il peut charger et retourner un assembly qui satisfait la requête.</span><span class="sxs-lookup"><span data-stu-id="30142-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="30142-118">La liste suivante décrit des exemples de scénarios.</span><span class="sxs-lookup"><span data-stu-id="30142-118">The following list describes some sample scenarios.</span></span>  
  
- <span data-ttu-id="30142-119">Si le gestionnaire connaît l’emplacement d’une version de l’assembly, il peut charger l’assembly à l’aide de la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>, et retourner l’assembly chargé si l’opération réussit.</span><span class="sxs-lookup"><span data-stu-id="30142-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
- <span data-ttu-id="30142-120">Si le gestionnaire a accès à une base de données d’assemblys stockés sous la forme de tableaux d’octets, il peut charger un tableau d’octets à l’aide de l’une des surcharges de méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> qui acceptent un tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="30142-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
- <span data-ttu-id="30142-121">Le gestionnaire peut générer un assembly dynamique et le retourner.</span><span class="sxs-lookup"><span data-stu-id="30142-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30142-122">Le gestionnaire doit charger l’assembly dans le contexte LoadFrom, dans le contexte de chargement ou sans contexte. Si le gestionnaire charge l’assembly dans le contexte ReflectionOnly à l’aide de la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> ou <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>, la tentative de chargement ayant déclenché l’événement <xref:System.AppDomain.AssemblyResolve> échoue.</span><span class="sxs-lookup"><span data-stu-id="30142-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="30142-123">Il appartient au gestionnaire d’événements de retourner un assembly approprié.</span><span class="sxs-lookup"><span data-stu-id="30142-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="30142-124">Le gestionnaire peut analyser le nom complet de l’assembly demandé en passant la valeur de propriété <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> au constructeur <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="30142-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="30142-125">À compter de .NET Framework 4, le gestionnaire peut utiliser la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> pour déterminer si la requête actuelle est une dépendance d’un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="30142-125">Beginning with the .NET Framework 4, the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="30142-126">Ces informations permettent d’identifier un assembly qui satisfait la dépendance.</span><span class="sxs-lookup"><span data-stu-id="30142-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="30142-127">Le gestionnaire d’événements peut retourner une version de l’assembly différente de celle qui a été demandée.</span><span class="sxs-lookup"><span data-stu-id="30142-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="30142-128">Dans la plupart des cas, l’assembly qui est retourné par le gestionnaire apparaît dans le contexte de chargement, indépendamment du contexte dans lequel le gestionnaire le charge.</span><span class="sxs-lookup"><span data-stu-id="30142-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="30142-129">Par exemple, si le gestionnaire utilise la méthode <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> pour charger un assembly dans le contexte LoadFrom, l’assembly apparaît dans le contexte de chargement quand le gestionnaire le retourne.</span><span class="sxs-lookup"><span data-stu-id="30142-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="30142-130">Toutefois, dans le cas suivant, l’assembly apparaît sans contexte quand le gestionnaire le retourne :</span><span class="sxs-lookup"><span data-stu-id="30142-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
- <span data-ttu-id="30142-131">le gestionnaire charge un assembly sans contexte ;</span><span class="sxs-lookup"><span data-stu-id="30142-131">The handler loads an assembly without context.</span></span>  
  
- <span data-ttu-id="30142-132">la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> n’a pas la valeur Null ;</span><span class="sxs-lookup"><span data-stu-id="30142-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
- <span data-ttu-id="30142-133">l’assembly demandeur (c’est-à-dire, l’assembly retourné par la propriété <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType>) a été chargé sans contexte.</span><span class="sxs-lookup"><span data-stu-id="30142-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="30142-134">Pour plus d’informations sur les contextes, consultez la surcharge de méthode <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="30142-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="30142-135">Vous pouvez charger plusieurs versions du même assembly dans le même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="30142-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="30142-136">Cette pratique n’est pas recommandée, car elle peut entraîner des problèmes d’assignation de type.</span><span class="sxs-lookup"><span data-stu-id="30142-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="30142-137">Voir [Les meilleures pratiques pour le chargement de l’assemblage](../../framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="30142-137">See [Best practices for assembly loading](../../framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="30142-138">Ce que le gestionnaire d’événements ne devrait pas faire</span><span class="sxs-lookup"><span data-stu-id="30142-138">What the event handler should not do</span></span>  
<span data-ttu-id="30142-139">La règle principale pour gérer l’événement <xref:System.AppDomain.AssemblyResolve> est que vous ne devez pas essayer de retourner un assembly que vous ne reconnaissez pas.</span><span class="sxs-lookup"><span data-stu-id="30142-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="30142-140">Quand vous écrivez le gestionnaire, vous devez avoir connaissance des assemblys qui peuvent provoquer le déclenchement de l’événement.</span><span class="sxs-lookup"><span data-stu-id="30142-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="30142-141">Votre gestionnaire doit retourner Null pour d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="30142-141">Your handler should return null for other assemblies.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="30142-142">À compter de .NET Framework 4, l’événement <xref:System.AppDomain.AssemblyResolve> est déclenché pour les assemblys satellites.</span><span class="sxs-lookup"><span data-stu-id="30142-142">Beginning with the .NET Framework 4, the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="30142-143">Ce changement affecte un gestionnaire d’événements qui a été écrit pour une version antérieure du .NET Framework, si le gestionnaire tente de résoudre toutes les requêtes de chargement d’assembly.</span><span class="sxs-lookup"><span data-stu-id="30142-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="30142-144">Les gestionnaires d’événements qui ignorent les assemblys non reconnus ne sont pas affectés par ce changement : ils retournent la valeur Null et les mécanismes de secours normaux sont suivis.</span><span class="sxs-lookup"><span data-stu-id="30142-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  

<span data-ttu-id="30142-145">Durant le chargement d’un assembly, le gestionnaire d’événements ne doit pas utiliser les surcharges de méthode <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> et <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> qui peuvent provoquer le déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve> de manière récursive, car cela peut provoquer un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="30142-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="30142-146">(Voir la liste fournie plus tôt dans ce sujet.) Cela se produit même si vous fournissez une manipulation d’exception pour la demande de charge, car aucune exception n’est lancée jusqu’à ce que tous les gestionnaires d’événements soient revenus.</span><span class="sxs-lookup"><span data-stu-id="30142-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="30142-147">Le code suivant provoque donc un dépassement de capacité de la pile si `MyAssembly` est introuvable :</span><span class="sxs-lookup"><span data-stu-id="30142-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="30142-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30142-148">See also</span></span>

- [<span data-ttu-id="30142-149">Meilleures pratiques pour le chargement de l’assemblage</span><span class="sxs-lookup"><span data-stu-id="30142-149">Best practices for assembly loading</span></span>](../../framework/deployment/best-practices-for-assembly-loading.md)
- [<span data-ttu-id="30142-150">Utiliser les domaines d’application</span><span class="sxs-lookup"><span data-stu-id="30142-150">Use application domains</span></span>](../../framework/app-domains/use.md)
