---
title: Wrapper pouvant être appelé par COM
ms.date: 10/23/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 601f9a216bc2e11ccb34f1f3b3df267002efb01f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631463"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="b448b-102">Wrapper pouvant être appelé par COM</span><span class="sxs-lookup"><span data-stu-id="b448b-102">COM Callable Wrapper</span></span>

<span data-ttu-id="b448b-103">Quand un client COM appelle un objet .NET, le common language runtime crée l'objet managé et un wrapper CCW pour cet objet.</span><span class="sxs-lookup"><span data-stu-id="b448b-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="b448b-104">Parce qu'ils ne peuvent pas référencer directement un objet .NET, les clients COM utilisent le wrapper CCW en tant que proxy pour l'objet managé.</span><span class="sxs-lookup"><span data-stu-id="b448b-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="b448b-105">Le runtime crée un unique wrapper CCW pour un objet managé, indépendamment du nombre de clients COM demandant ses services.</span><span class="sxs-lookup"><span data-stu-id="b448b-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="b448b-106">Comme le montre l'illustration suivante, plusieurs clients COM peuvent contenir une référence au wrapper CCW qui expose l'interface INew.</span><span class="sxs-lookup"><span data-stu-id="b448b-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="b448b-107">Le wrapper CCW contient quant à lui une référence à l'objet managé qui implémente l'interface et fait l'objet d'un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b448b-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="b448b-108">Les clients COM et .NET peuvent envoyer simultanément des requêtes au même objet managé.</span><span class="sxs-lookup"><span data-stu-id="b448b-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Plusieurs clients COM contenant une référence au wrapper CCW qui expose INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="b448b-110">Les wrappers CCW ne sont pas visibles par les autres classes qui s’exécutent dans le runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="b448b-110">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="b448b-111">Leur objectif principal est de marshaler les appels entre code managé et code non managé. Cependant, les wrappers CCW gèrent également l'identité et la durée de vie des objets managés qu'ils encapsulent.</span><span class="sxs-lookup"><span data-stu-id="b448b-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="b448b-112">Identité d'un objet</span><span class="sxs-lookup"><span data-stu-id="b448b-112">Object Identity</span></span>

<span data-ttu-id="b448b-113">Le runtime alloue de la mémoire pour l'objet .NET depuis son tas collecté, ce qui permet au runtime de déplacer l'objet au sein de la mémoire selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="b448b-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="b448b-114">En revanche, le runtime alloue de la mémoire pour le wrapper CCW depuis un tas non collecté, permettant ainsi aux clients COM de faire directement référence au wrapper.</span><span class="sxs-lookup"><span data-stu-id="b448b-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="b448b-115">Durée de vie des objets</span><span class="sxs-lookup"><span data-stu-id="b448b-115">Object Lifetime</span></span>

<span data-ttu-id="b448b-116">Contrairement au client .NET qu'il encapsule, le wrapper CCW fait l'objet d'un comptage de références comme dans COM.</span><span class="sxs-lookup"><span data-stu-id="b448b-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="b448b-117">Quand le nombre de références du wrapper CCW atteint zéro, le wrapper libère sa référence à l'objet managé.</span><span class="sxs-lookup"><span data-stu-id="b448b-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="b448b-118">Un objet managé sans aucune référence restante sera collecté lors du prochain cycle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="b448b-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="b448b-119">Simulation d'interfaces COM</span><span class="sxs-lookup"><span data-stu-id="b448b-119">Simulating COM interfaces</span></span>

<span data-ttu-id="b448b-120">CCW expose aux clients COM l’ensemble des interfaces, types de données et valeurs de retour publics et visibles par COM d’une manière qui est cohérente avec l’application de COM de l’interaction reposant sur l’interface.</span><span class="sxs-lookup"><span data-stu-id="b448b-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="b448b-121">Pour un client COM, l’appel de méthodes sur un objet .NET est identique à l’appel de méthodes sur un objet COM.</span><span class="sxs-lookup"><span data-stu-id="b448b-121">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="b448b-122">Pour adopter cette approche transparente, le wrapper CCW fabrique des interfaces COM classiques, comme **IUnknown** et **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="b448b-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="b448b-123">Comme le montre l'illustration suivante, le wrapper CCW contient une référence unique sur l'objet .NET qu'il encapsule.</span><span class="sxs-lookup"><span data-stu-id="b448b-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="b448b-124">Le client COM et l’objet .NET interagissent via le proxy et la construction stub du wrapper CCW.</span><span class="sxs-lookup"><span data-stu-id="b448b-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagramme illustrant la façon dont le wrapper CCW fabrique des interfaces COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="b448b-126">Outre l’exposition des interfaces qui sont implémentées explicitement par une classe dans l’environnement managé, le runtime .NET fournit également des implémentations des interfaces COM répertoriées dans le tableau suivant, pour le compte de l’objet.</span><span class="sxs-lookup"><span data-stu-id="b448b-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="b448b-127">Une classe .NET peut substituer le comportement par défaut par sa propre implémentation de ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="b448b-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="b448b-128">Toutefois, le runtime fournit toujours l’implémentation pour les interfaces **IUnknown** et **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="b448b-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="b448b-129">Interface</span><span class="sxs-lookup"><span data-stu-id="b448b-129">Interface</span></span>|<span data-ttu-id="b448b-130">Description</span><span class="sxs-lookup"><span data-stu-id="b448b-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b448b-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="b448b-131">**IDispatch**</span></span>|<span data-ttu-id="b448b-132">Fournit un mécanisme de liaison tardive au type.</span><span class="sxs-lookup"><span data-stu-id="b448b-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="b448b-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="b448b-133">**IErrorInfo**</span></span>|<span data-ttu-id="b448b-134">Fournit une description textuelle de l’erreur, sa source, un fichier d’aide, un contexte d’aide et le GUID de l’interface ayant défini l’erreur (toujours **GUID_NULL** pour les classes .NET).</span><span class="sxs-lookup"><span data-stu-id="b448b-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="b448b-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="b448b-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="b448b-136">Permet aux clients COM d’accéder à l’interface **ITypeInfo** implémentée par une classe managée.</span><span class="sxs-lookup"><span data-stu-id="b448b-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="b448b-137">Retourne `COR_E_NOTSUPPORTED` sur .NET Core pour les types non importés à partir de COM.</span><span class="sxs-lookup"><span data-stu-id="b448b-137">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="b448b-138">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="b448b-138">**ISupportErrorInfo**</span></span>|<span data-ttu-id="b448b-139">Permet à un client COM de déterminer si l’objet managé prend en charge l’interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="b448b-139">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="b448b-140">Dans ce cas, il permet au client d'obtenir un pointeur vers le dernier objet exception.</span><span class="sxs-lookup"><span data-stu-id="b448b-140">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="b448b-141">Tous les types managés prennent en charge l’interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="b448b-141">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="b448b-142">**ITypeInfo** (.NET Framework uniquement)</span><span class="sxs-lookup"><span data-stu-id="b448b-142">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="b448b-143">Fournit des informations de type pour une classe qui sont les mêmes que celles fournies par Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="b448b-143">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="b448b-144">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="b448b-144">**IUnknown**</span></span>|<span data-ttu-id="b448b-145">Fournit l’implémentation standard de l’interface **IUnknown** avec laquelle le client COM gère la durée de vie du wrapper CCW et fournit le forçage de type.</span><span class="sxs-lookup"><span data-stu-id="b448b-145">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="b448b-146">Une classe managée peut également fournir les interfaces COM décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b448b-146">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="b448b-147">Interface</span><span class="sxs-lookup"><span data-stu-id="b448b-147">Interface</span></span>|<span data-ttu-id="b448b-148">Description</span><span class="sxs-lookup"><span data-stu-id="b448b-148">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b448b-149">Interface de la classe (\_*nomclasse*)</span><span class="sxs-lookup"><span data-stu-id="b448b-149">The (\_*classname*) class interface</span></span>|<span data-ttu-id="b448b-150">Interface, exposée par le runtime et non définie explicitement, qui expose l'ensemble des interfaces, méthodes, propriétés et champs publics qui sont exposés explicitement sur un objet managé.</span><span class="sxs-lookup"><span data-stu-id="b448b-150">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="b448b-151">**IConnectionPoint** et **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="b448b-151">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="b448b-152">Interface pour les objets qui émettent des événements basés sur les délégués (interface pour l'inscription des abonnés d'événements).</span><span class="sxs-lookup"><span data-stu-id="b448b-152">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="b448b-153">**IDispatchEx** (.NET Framework uniquement)</span><span class="sxs-lookup"><span data-stu-id="b448b-153">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="b448b-154">Interface fournie par le runtime si la classe implémente **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="b448b-154">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="b448b-155">L’interface **IDispatchEx** est une extension de l’interface **IDispatch** qui, contrairement à l’interface **IDispatch**, permet l’énumération, l’ajout, la suppression et l’appel de la casse des membres.</span><span class="sxs-lookup"><span data-stu-id="b448b-155">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="b448b-156">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="b448b-156">**IEnumVARIANT**</span></span>|<span data-ttu-id="b448b-157">Interface pour les classes de type collection, qui énumère les objets d’une collection si la classe implémente **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="b448b-157">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="b448b-158">Présentation de l'interface de classe</span><span class="sxs-lookup"><span data-stu-id="b448b-158">Introducing the class interface</span></span>

<span data-ttu-id="b448b-159">L'interface de classe, qui n'est pas explicitement définie dans le code managé, est une interface qui expose l'ensemble des méthodes, propriétés, champs et événements publics qui sont exposés explicitement sur l'objet .NET.</span><span class="sxs-lookup"><span data-stu-id="b448b-159">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="b448b-160">Cette interface peut être double ou dispatch uniquement.</span><span class="sxs-lookup"><span data-stu-id="b448b-160">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="b448b-161">L'interface de classe reçoit le nom de la classe .NET, précédé d'un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="b448b-161">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="b448b-162">Par exemple, pour la classe Mammal, l’interface de classe est \_Mammal.</span><span class="sxs-lookup"><span data-stu-id="b448b-162">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="b448b-163">Pour les classes dérivées, l'interface de classe expose l'ensemble des méthodes, propriétés et champs publics de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="b448b-163">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="b448b-164">La classe dérivée expose également une interface de classe pour chaque classe de base.</span><span class="sxs-lookup"><span data-stu-id="b448b-164">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="b448b-165">Par exemple, si la classe Mammal étend la classe MammalSuperclass, qui elle-même étend System.Object, l’objet .NET expose aux clients COM trois interfaces de classe nommées \_Mammal, \_MammalSuperclass et \_Object.</span><span class="sxs-lookup"><span data-stu-id="b448b-165">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="b448b-166">Regardons, par exemple, la classe .NET suivante :</span><span class="sxs-lookup"><span data-stu-id="b448b-166">For example, consider the following .NET class:</span></span>

```vb
' Applies the ClassInterfaceAttribute to set the interface to dual.
<ClassInterface(ClassInterfaceType.AutoDual)> _
' Implicitly extends System.Object.
Public Class Mammal
    Sub Eat()
    Sub Breathe()
    Sub Sleep()
End Class
```

```csharp
// Applies the ClassInterfaceAttribute to set the interface to dual.
[ClassInterface(ClassInterfaceType.AutoDual)]
// Implicitly extends System.Object.
public class Mammal
{
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

<span data-ttu-id="b448b-167">Le client COM peut obtenir un pointeur vers une interface de classe nommée `_Mammal`.</span><span class="sxs-lookup"><span data-stu-id="b448b-167">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="b448b-168">Sur .NET Framework, vous pouvez utiliser l’outil [Exportateur de bibliothèques de types (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) pour générer une bibliothèque de types contenant la définition de l’interface `_Mammal`.</span><span class="sxs-lookup"><span data-stu-id="b448b-168">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="b448b-169">L’exportateur de bibliothèques de types n’est pas pris en charge sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b448b-169">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="b448b-170">Si la classe `Mammal` implémentait une ou plusieurs interfaces, les interfaces apparaîtraient sous la coclasse.</span><span class="sxs-lookup"><span data-stu-id="b448b-170">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

```
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]
interface _Mammal : IDispatch
{
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*
        pRetVal);
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]
        VARIANT_BOOL* pRetVal);
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);
    [id(0x6002000d)] HRESULT Eat();
    [id(0x6002000e)] HRESULT Breathe();
    [id(0x6002000f)] HRESULT Sleep();
}
[uuid(…)]
coclass Mammal
{
    [default] interface _Mammal;
}
```

<span data-ttu-id="b448b-171">La génération de l'interface de classe est facultative.</span><span class="sxs-lookup"><span data-stu-id="b448b-171">Generating the class interface is optional.</span></span> <span data-ttu-id="b448b-172">Par défaut, COM Interop génère une interface de dispatch pour chaque classe que vous exportez vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b448b-172">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="b448b-173">Vous pouvez empêcher ou modifier la création automatique de cette interface en appliquant <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à votre classe.</span><span class="sxs-lookup"><span data-stu-id="b448b-173">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="b448b-174">Même si l'interface de classe simplifie l'exposition des classes managées à COM, ses utilisations sont limitées.</span><span class="sxs-lookup"><span data-stu-id="b448b-174">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="b448b-175">L'utilisation de l'interface de classe, au lieu de définir explicitement la vôtre, peut compliquer le contrôle de version de votre classe managée.</span><span class="sxs-lookup"><span data-stu-id="b448b-175">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="b448b-176">Lisez les instructions suivantes avant d'utiliser l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="b448b-176">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="b448b-177">Définissez une interface explicite pour les clients COM plutôt que de générer l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="b448b-177">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="b448b-178">Étant donné que COM Interop génère automatiquement une interface de classe, les modifications après version apportées à votre classe peuvent modifier la disposition de l'interface de classe exposée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="b448b-178">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="b448b-179">Étant donné que les clients COM ne sont généralement pas préparés à gérer les modifications apportées à la disposition d'une interface, ils s'arrêtent si vous modifiez la disposition des membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="b448b-179">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="b448b-180">Cette règle renforce l'idée que les interfaces exposées aux clients COM doivent rester intactes.</span><span class="sxs-lookup"><span data-stu-id="b448b-180">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="b448b-181">Pour réduire le risque d'arrêt des clients COM en réorganisant par inadvertance la disposition de l'interface, isolez toutes les modifications apportées à la classe à partir de la disposition de l'interface en définissant explicitement les interfaces.</span><span class="sxs-lookup"><span data-stu-id="b448b-181">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="b448b-182">Utilisez **ClassInterfaceAttribute** pour désactiver la génération automatique de l’interface de classe et implémenter une interface explicite de la classe, comme dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="b448b-182">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

<span data-ttu-id="b448b-183">La valeur **ClassInterfaceType.None** empêche l’interface de classe d’être générée quand les métadonnées de classe sont exportées vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b448b-183">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="b448b-184">Dans l'exemple précédent, les clients COM peuvent accéder à la classe `LoanApp` uniquement via l'interface `IExplicit`.</span><span class="sxs-lookup"><span data-stu-id="b448b-184">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="b448b-185">Éviter de mettre en cache des identificateurs de dispatch (DISPID)</span><span class="sxs-lookup"><span data-stu-id="b448b-185">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="b448b-186">L'utilisation de l'interface de classe est une option acceptable pour les clients par script, les clients Microsoft Visual Basic 6.0 ou tout client à liaison tardive qui ne met pas en cache les DISPID des membres d'interface.</span><span class="sxs-lookup"><span data-stu-id="b448b-186">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="b448b-187">Les DISPID identifient les membres d’interface pour permettre la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="b448b-187">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="b448b-188">Pour l'interface de classe, la génération de DISPID repose sur la position du membre de l'interface.</span><span class="sxs-lookup"><span data-stu-id="b448b-188">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="b448b-189">Si vous modifiez l'ordre du membre et exportez la classe vers une bibliothèque de types, vous modifierez les DISPID générés dans l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="b448b-189">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="b448b-190">Pour éviter l’arrêt des clients COM à liaison tardive lors de l’utilisation de l’interface de classe, appliquez **ClassInterfaceAttribute** avec la valeur **ClassInterfaceType.AutoDispatch**.</span><span class="sxs-lookup"><span data-stu-id="b448b-190">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="b448b-191">Cette valeur implémente une interface de classe de dispatch, mais omet la description de l'interface de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="b448b-191">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="b448b-192">Sans description d'interface, les clients sont incapables de mettre en cache les DISPID au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b448b-192">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="b448b-193">Même s'il s'agit du type d'interface par défaut pour l'interface de classe, vous pouvez appliquer explicitement la valeur d'attribut.</span><span class="sxs-lookup"><span data-stu-id="b448b-193">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

<span data-ttu-id="b448b-194">Pour obtenir le DISPID d’un membre d’interface au moment de l’exécution, les clients COM peuvent appeler **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="b448b-194">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="b448b-195">Pour appeler une méthode sur l’interface, passez le DISPID retourné comme argument à **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="b448b-195">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="b448b-196">Limitez l'utilisation de l'option d'interface double pour l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="b448b-196">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="b448b-197">Les interfaces doubles permettent une liaison anticipée et tardive aux membres d’interface par les clients COM.</span><span class="sxs-lookup"><span data-stu-id="b448b-197">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="b448b-198">Au moment du design et au cours des tests, il peut s'avérer utile de faire de l'interface de classe une interface double.</span><span class="sxs-lookup"><span data-stu-id="b448b-198">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="b448b-199">Pour une classe managée (et ses classes de base) qui ne sera jamais modifiée, cette option est également acceptable.</span><span class="sxs-lookup"><span data-stu-id="b448b-199">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="b448b-200">Dans tous les autres cas, évitez d'utiliser l'interface double.</span><span class="sxs-lookup"><span data-stu-id="b448b-200">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="b448b-201">Une interface double générée automatiquement peut être appropriée dans de rares cas. Toutefois, cela rend souvent le contrôle de version plus complexe.</span><span class="sxs-lookup"><span data-stu-id="b448b-201">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="b448b-202">Par exemple, les clients COM qui utilisent l'interface de classe d'une classe dérivée peuvent facilement s'arrêter en raison des modifications apportées à la classe de base.</span><span class="sxs-lookup"><span data-stu-id="b448b-202">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="b448b-203">Quand une tierce partie fournit la classe de base, la disposition de l'interface de classe est hors de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="b448b-203">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="b448b-204">De plus, contrairement à une interface Dispatch uniquement, une interface Dual (**ClassInterfaceType.AutoDual**) offre une description de l’interface de classe dans la bibliothèque de types exportée.</span><span class="sxs-lookup"><span data-stu-id="b448b-204">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="b448b-205">Une telle description encourage les clients à liaison tardive à mettre en cache les DISPID au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b448b-205">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="b448b-206">Vérifiez que toutes les notifications d’événements COM sont à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="b448b-206">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="b448b-207">Par défaut, les informations du type COM sont intégrées directement aux assemblys managés, ce qui éviter d’avoir à utiliser des assemblys PIA (Primary Interop Assembly).</span><span class="sxs-lookup"><span data-stu-id="b448b-207">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="b448b-208">Les informations de type incorporées présentent toutefois une limitation : elles ne prennent pas en charge la distribution des notifications d’événements COM par des appels vtable à liaison anticipée, mais seulement par des appels `IDispatch::Invoke` à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="b448b-208">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="b448b-209">Si votre application exige des appels à liaison anticipée à des méthodes d’interface d’événements COM, vous pouvez définir la propriété **Incorporer les types Interop** sur `true` dans Visual Studio, ou inclure l’élément suivant dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="b448b-209">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="b448b-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b448b-210">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="b448b-211">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="b448b-211">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="b448b-212">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="b448b-212">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="b448b-213">Exposition de composants .NET Core à COM</span><span class="sxs-lookup"><span data-stu-id="b448b-213">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="b448b-214">Qualifier des types .NET pour l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="b448b-214">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="b448b-215">Wrapper pouvant être appelé par le runtime</span><span class="sxs-lookup"><span data-stu-id="b448b-215">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
