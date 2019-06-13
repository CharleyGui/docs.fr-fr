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
ms.openlocfilehash: a658a9f706a53697b341463b443c5145a727b4b9
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758255"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="5d2d1-102">Wrapper pouvant être appelé par COM</span><span class="sxs-lookup"><span data-stu-id="5d2d1-102">COM Callable Wrapper</span></span>

<span data-ttu-id="5d2d1-103">Quand un client COM appelle un objet .NET, le common language runtime crée l'objet managé et un wrapper CCW pour cet objet.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="5d2d1-104">Parce qu'ils ne peuvent pas référencer directement un objet .NET, les clients COM utilisent le wrapper CCW en tant que proxy pour l'objet managé.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="5d2d1-105">Le runtime crée un unique wrapper CCW pour un objet managé, indépendamment du nombre de clients COM demandant ses services.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="5d2d1-106">Comme le montre l'illustration suivante, plusieurs clients COM peuvent contenir une référence au wrapper CCW qui expose l'interface INew.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="5d2d1-107">Le wrapper CCW contient quant à lui une référence à l'objet managé qui implémente l'interface et fait l'objet d'un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="5d2d1-108">Les clients COM et .NET peuvent envoyer simultanément des requêtes au même objet managé.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Plusieurs clients COM contenant une référence au wrapper CCW qui expose INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="5d2d1-110">Les wrappers CCW ne sont pas visibles par les autres classes qui s'exécutent dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-110">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="5d2d1-111">Leur objectif principal est de marshaler les appels entre code managé et code non managé. Cependant, les wrappers CCW gèrent également l'identité et la durée de vie des objets managés qu'ils encapsulent.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="5d2d1-112">Identité d'un objet</span><span class="sxs-lookup"><span data-stu-id="5d2d1-112">Object Identity</span></span>

<span data-ttu-id="5d2d1-113">Le runtime alloue de la mémoire pour l'objet .NET depuis son tas collecté, ce qui permet au runtime de déplacer l'objet au sein de la mémoire selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="5d2d1-114">En revanche, le runtime alloue de la mémoire pour le wrapper CCW depuis un tas non collecté, permettant ainsi aux clients COM de faire directement référence au wrapper.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="5d2d1-115">Durée de vie des objets</span><span class="sxs-lookup"><span data-stu-id="5d2d1-115">Object Lifetime</span></span>

<span data-ttu-id="5d2d1-116">Contrairement au client .NET qu'il encapsule, le wrapper CCW fait l'objet d'un comptage de références comme dans COM.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="5d2d1-117">Quand le nombre de références du wrapper CCW atteint zéro, le wrapper libère sa référence à l'objet managé.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="5d2d1-118">Un objet managé sans aucune référence restante sera collecté lors du prochain cycle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="5d2d1-119">Simulation d'interfaces COM</span><span class="sxs-lookup"><span data-stu-id="5d2d1-119">Simulating COM interfaces</span></span>

<span data-ttu-id="5d2d1-120">CCW expose aux clients COM l’ensemble des interfaces, types de données et valeurs de retour publics et visibles par COM d’une manière qui est cohérente avec l’application de COM de l’interaction reposant sur l’interface.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="5d2d1-121">Pour un client COM, l'appel de méthodes sur un objet .NET Framework est identique à l'appel de méthodes sur un objet COM</span><span class="sxs-lookup"><span data-stu-id="5d2d1-121">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="5d2d1-122">Pour adopter cette approche transparente, le wrapper CCW fabrique des interfaces COM classiques, comme **IUnknown** et **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="5d2d1-123">Comme le montre l'illustration suivante, le wrapper CCW contient une référence unique sur l'objet .NET qu'il encapsule.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="5d2d1-124">Le client COM et l’objet .NET interagissent via le proxy et la construction stub du wrapper CCW.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagramme illustrant la façon dont le wrapper CCW fabrique des interfaces COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="5d2d1-126">Outre l'exposition des interfaces qui sont implémentées explicitement par une classe dans l'environnement managé, .NET Framework fournit également des implémentations des interfaces COM répertoriées dans le tableau suivant, pour le compte de l'objet.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="5d2d1-127">Une classe .NET peut substituer le comportement par défaut par sa propre implémentation de ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="5d2d1-128">Toutefois, le runtime fournit toujours l’implémentation pour les interfaces **IUnknown** et **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="5d2d1-129">Interface</span><span class="sxs-lookup"><span data-stu-id="5d2d1-129">Interface</span></span>|<span data-ttu-id="5d2d1-130">Description</span><span class="sxs-lookup"><span data-stu-id="5d2d1-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="5d2d1-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-131">**IDispatch**</span></span>|<span data-ttu-id="5d2d1-132">Fournit un mécanisme de liaison tardive au type.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="5d2d1-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-133">**IErrorInfo**</span></span>|<span data-ttu-id="5d2d1-134">Fournit une description textuelle de l’erreur, sa source, un fichier d’aide, un contexte d’aide et le GUID de l’interface ayant défini l’erreur (toujours **GUID_NULL** pour les classes .NET).</span><span class="sxs-lookup"><span data-stu-id="5d2d1-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="5d2d1-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="5d2d1-136">Permet aux clients COM d’accéder à l’interface **ITypeInfo** implémentée par une classe managée.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|
|<span data-ttu-id="5d2d1-137">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-137">**ISupportErrorInfo**</span></span>|<span data-ttu-id="5d2d1-138">Permet à un client COM de déterminer si l’objet managé prend en charge l’interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-138">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="5d2d1-139">Dans ce cas, il permet au client d'obtenir un pointeur vers le dernier objet exception.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-139">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="5d2d1-140">Tous les types managés prennent en charge l’interface **IErrorInfo**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-140">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="5d2d1-141">**ITypeInfo**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-141">**ITypeInfo**</span></span>|<span data-ttu-id="5d2d1-142">Fournit des informations de type pour une classe qui sont les mêmes que celles fournies par Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-142">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="5d2d1-143">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-143">**IUnknown**</span></span>|<span data-ttu-id="5d2d1-144">Fournit l’implémentation standard de l’interface **IUnknown** avec laquelle le client COM gère la durée de vie du wrapper CCW et fournit le forçage de type.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-144">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="5d2d1-145">Une classe managée peut également fournir les interfaces COM décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-145">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="5d2d1-146">Interface</span><span class="sxs-lookup"><span data-stu-id="5d2d1-146">Interface</span></span>|<span data-ttu-id="5d2d1-147">Description</span><span class="sxs-lookup"><span data-stu-id="5d2d1-147">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="5d2d1-148">Interface de la classe (\_*nomclasse*)</span><span class="sxs-lookup"><span data-stu-id="5d2d1-148">The (\_*classname*) class interface</span></span>|<span data-ttu-id="5d2d1-149">Interface, exposée par le runtime et non définie explicitement, qui expose l'ensemble des interfaces, méthodes, propriétés et champs publics qui sont exposés explicitement sur un objet managé.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-149">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="5d2d1-150">**IConnectionPoint** et **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-150">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="5d2d1-151">Interface pour les objets qui émettent des événements basés sur les délégués (interface pour l'inscription des abonnés d'événements).</span><span class="sxs-lookup"><span data-stu-id="5d2d1-151">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="5d2d1-152">**IDispatchEx**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-152">**IDispatchEx**</span></span>|<span data-ttu-id="5d2d1-153">Interface fournie par le runtime si la classe implémente **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-153">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="5d2d1-154">L’interface **IDispatchEx** est une extension de l’interface **IDispatch** qui, contrairement à l’interface **IDispatch**, permet l’énumération, l’ajout, la suppression et l’appel de la casse des membres.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-154">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="5d2d1-155">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="5d2d1-155">**IEnumVARIANT**</span></span>|<span data-ttu-id="5d2d1-156">Interface pour les classes de type collection, qui énumère les objets d’une collection si la classe implémente **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-156">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="5d2d1-157">Présentation de l'interface de classe</span><span class="sxs-lookup"><span data-stu-id="5d2d1-157">Introducing the class interface</span></span>

<span data-ttu-id="5d2d1-158">L'interface de classe, qui n'est pas explicitement définie dans le code managé, est une interface qui expose l'ensemble des méthodes, propriétés, champs et événements publics qui sont exposés explicitement sur l'objet .NET.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-158">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="5d2d1-159">Cette interface peut être double ou dispatch uniquement.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-159">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="5d2d1-160">L'interface de classe reçoit le nom de la classe .NET, précédé d'un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-160">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="5d2d1-161">Par exemple, pour la classe Mammal, l’interface de classe est \_Mammal.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-161">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="5d2d1-162">Pour les classes dérivées, l'interface de classe expose l'ensemble des méthodes, propriétés et champs publics de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-162">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="5d2d1-163">La classe dérivée expose également une interface de classe pour chaque classe de base.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-163">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="5d2d1-164">Par exemple, si la classe Mammal étend la classe MammalSuperclass, qui elle-même étend System.Object, l’objet .NET expose aux clients COM trois interfaces de classe nommées \_Mammal, \_MammalSuperclass et \_Object.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-164">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="5d2d1-165">Regardons, par exemple, la classe .NET suivante :</span><span class="sxs-lookup"><span data-stu-id="5d2d1-165">For example, consider the following .NET class:</span></span>

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

<span data-ttu-id="5d2d1-166">Le client COM peut obtenir un pointeur vers une interface de classe nommée `_Mammal`, qui est décrite dans la bibliothèque de types générée par l’outil [Tlbexp.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="5d2d1-166">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="5d2d1-167">Si la classe `Mammal` implémentait une ou plusieurs interfaces, les interfaces apparaîtraient sous la coclasse.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-167">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="5d2d1-168">La génération de l'interface de classe est facultative.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-168">Generating the class interface is optional.</span></span> <span data-ttu-id="5d2d1-169">Par défaut, COM Interop génère une interface de dispatch pour chaque classe que vous exportez vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-169">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="5d2d1-170">Vous pouvez empêcher ou modifier la création automatique de cette interface en appliquant <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> à votre classe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-170">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="5d2d1-171">Même si l'interface de classe simplifie l'exposition des classes managées à COM, ses utilisations sont limitées.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-171">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="5d2d1-172">L'utilisation de l'interface de classe, au lieu de définir explicitement la vôtre, peut compliquer le contrôle de version de votre classe managée.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-172">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="5d2d1-173">Lisez les instructions suivantes avant d'utiliser l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-173">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="5d2d1-174">Définissez une interface explicite pour les clients COM plutôt que de générer l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-174">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="5d2d1-175">Étant donné que COM Interop génère automatiquement une interface de classe, les modifications après version apportées à votre classe peuvent modifier la disposition de l'interface de classe exposée par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-175">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="5d2d1-176">Étant donné que les clients COM ne sont généralement pas préparés à gérer les modifications apportées à la disposition d'une interface, ils s'arrêtent si vous modifiez la disposition des membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-176">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="5d2d1-177">Cette règle renforce l'idée que les interfaces exposées aux clients COM doivent rester intactes.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-177">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="5d2d1-178">Pour réduire le risque d'arrêt des clients COM en réorganisant par inadvertance la disposition de l'interface, isolez toutes les modifications apportées à la classe à partir de la disposition de l'interface en définissant explicitement les interfaces.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-178">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="5d2d1-179">Utilisez **ClassInterfaceAttribute** pour désactiver la génération automatique de l’interface de classe et implémenter une interface explicite de la classe, comme dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="5d2d1-179">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

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

<span data-ttu-id="5d2d1-180">La valeur **ClassInterfaceType.None** empêche l’interface de classe d’être générée quand les métadonnées de classe sont exportées vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-180">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="5d2d1-181">Dans l'exemple précédent, les clients COM peuvent accéder à la classe `LoanApp` uniquement via l'interface `IExplicit`.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-181">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="5d2d1-182">Éviter de mettre en cache des identificateurs de dispatch (DISPID)</span><span class="sxs-lookup"><span data-stu-id="5d2d1-182">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="5d2d1-183">L'utilisation de l'interface de classe est une option acceptable pour les clients par script, les clients Microsoft Visual Basic 6.0 ou tout client à liaison tardive qui ne met pas en cache les DISPID des membres d'interface.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-183">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="5d2d1-184">Les DISPID identifient les membres d’interface pour permettre la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-184">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="5d2d1-185">Pour l'interface de classe, la génération de DISPID repose sur la position du membre de l'interface.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-185">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="5d2d1-186">Si vous modifiez l'ordre du membre et exportez la classe vers une bibliothèque de types, vous modifierez les DISPID générés dans l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-186">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="5d2d1-187">Pour éviter l’arrêt des clients COM à liaison tardive lors de l’utilisation de l’interface de classe, appliquez **ClassInterfaceAttribute** avec la valeur **ClassInterfaceType.AutoDispatch**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-187">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="5d2d1-188">Cette valeur implémente une interface de classe de dispatch, mais omet la description de l'interface de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-188">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="5d2d1-189">Sans description d'interface, les clients sont incapables de mettre en cache les DISPID au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-189">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="5d2d1-190">Même s'il s'agit du type d'interface par défaut pour l'interface de classe, vous pouvez appliquer explicitement la valeur d'attribut.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-190">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

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

<span data-ttu-id="5d2d1-191">Pour obtenir le DISPID d’un membre d’interface au moment de l’exécution, les clients COM peuvent appeler **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-191">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="5d2d1-192">Pour appeler une méthode sur l’interface, passez le DISPID retourné comme argument à **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-192">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="5d2d1-193">Limitez l'utilisation de l'option d'interface double pour l'interface de classe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-193">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="5d2d1-194">Les interfaces doubles permettent une liaison anticipée et tardive aux membres d’interface par les clients COM.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-194">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="5d2d1-195">Au moment du design et au cours des tests, il peut s'avérer utile de faire de l'interface de classe une interface double.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-195">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="5d2d1-196">Pour une classe managée (et ses classes de base) qui ne sera jamais modifiée, cette option est également acceptable.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-196">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="5d2d1-197">Dans tous les autres cas, évitez d'utiliser l'interface double.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-197">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="5d2d1-198">Une interface double générée automatiquement peut être appropriée dans de rares cas. Toutefois, cela rend souvent le contrôle de version plus complexe.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-198">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="5d2d1-199">Par exemple, les clients COM qui utilisent l'interface de classe d'une classe dérivée peuvent facilement s'arrêter en raison des modifications apportées à la classe de base.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-199">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="5d2d1-200">Quand une tierce partie fournit la classe de base, la disposition de l'interface de classe est hors de votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-200">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="5d2d1-201">De plus, contrairement à une interface Dispatch uniquement, une interface Dual (**ClassInterfaceType.AutoDual**) offre une description de l’interface de classe dans la bibliothèque de types exportée.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-201">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="5d2d1-202">Une telle description encourage les clients à liaison tardive à mettre en cache les DISPID au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-202">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="5d2d1-203">Vérifiez que toutes les notifications d’événements COM sont à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-203">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="5d2d1-204">Par défaut, les informations du type COM sont intégrées directement aux assemblys managés, ce qui éviter d’avoir à utiliser des assemblys PIA (Primary Interop Assembly).</span><span class="sxs-lookup"><span data-stu-id="5d2d1-204">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="5d2d1-205">Toutefois, une des limitations des informations de type incorporées est qu’il ne prend pas en charge la remise de notifications d’événements COM par des appels à liaison anticipée vtable, mais prend uniquement en charge à liaison tardive `IDispatch::Invoke` appels.</span><span class="sxs-lookup"><span data-stu-id="5d2d1-205">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="5d2d1-206">Si votre application exige des appels à liaison anticipée à des méthodes d’interface d’événements COM, vous pouvez définir la propriété **Incorporer les types Interop** sur `true` dans Visual Studio, ou inclure l’élément suivant dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="5d2d1-206">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="5d2d1-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d2d1-207">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="5d2d1-208">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="5d2d1-208">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="5d2d1-209">Exposition de composants .NET Framework à COM</span><span class="sxs-lookup"><span data-stu-id="5d2d1-209">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="5d2d1-210">Qualifier des types .NET pour l'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="5d2d1-210">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="5d2d1-211">Wrapper pouvant être appelé par le runtime</span><span class="sxs-lookup"><span data-stu-id="5d2d1-211">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
