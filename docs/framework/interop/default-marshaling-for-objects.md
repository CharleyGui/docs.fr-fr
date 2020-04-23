---
title: Marshaling par défaut pour les objets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: e0de715a3ed33eedf212fc3e0e9930c9cbaa0a38
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123587"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="89e99-102">Marshaling par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="89e99-102">Default Marshaling for Objects</span></span>

<span data-ttu-id="89e99-103">Les paramètres et les champs de type <xref:System.Object?displayProperty=nameWithType> peuvent être exposés à un code non managé sous la forme de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="89e99-103">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="89e99-104">Un variant quand l’objet est un paramètre.</span><span class="sxs-lookup"><span data-stu-id="89e99-104">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="89e99-105">Une interface quand l’objet est un champ de structure.</span><span class="sxs-lookup"><span data-stu-id="89e99-105">An interface when the object is a structure field.</span></span>

<span data-ttu-id="89e99-106">Seul COM interop prend en charge le marshaling des types d’objets.</span><span class="sxs-lookup"><span data-stu-id="89e99-106">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="89e99-107">Le comportement par défaut est de marshaler des objets vers des variants COM.</span><span class="sxs-lookup"><span data-stu-id="89e99-107">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="89e99-108">Ces règles s’appliquent uniquement au type **Object** et ne s’appliquent pas aux objets fortement typés issus de la classe **Object**.</span><span class="sxs-lookup"><span data-stu-id="89e99-108">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="89e99-109">Options de marshaling</span><span class="sxs-lookup"><span data-stu-id="89e99-109">Marshaling Options</span></span>

<span data-ttu-id="89e99-110">Le tableau suivant montre les options de marshaling pour le type de données **Object**.</span><span class="sxs-lookup"><span data-stu-id="89e99-110">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="89e99-111">L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d’énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler des objets.</span><span class="sxs-lookup"><span data-stu-id="89e99-111">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="89e99-112">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="89e99-112">Enumeration type</span></span>|<span data-ttu-id="89e99-113">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="89e99-113">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="89e99-114">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="89e99-114">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="89e99-115">(valeur par défaut des paramètres)</span><span class="sxs-lookup"><span data-stu-id="89e99-115">(default for parameters)</span></span>|<span data-ttu-id="89e99-116">Variant de style COM.</span><span class="sxs-lookup"><span data-stu-id="89e99-116">A COM-style variant.</span></span>|
|<span data-ttu-id="89e99-117">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="89e99-117">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="89e99-118">Interface **IDispatch**, si possible ; sinon, interface **IUnknown**.</span><span class="sxs-lookup"><span data-stu-id="89e99-118">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="89e99-119">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="89e99-119">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="89e99-120">(valeur par défaut des champs)</span><span class="sxs-lookup"><span data-stu-id="89e99-120">(default for fields)</span></span>|<span data-ttu-id="89e99-121">Interface **IUnknown**.</span><span class="sxs-lookup"><span data-stu-id="89e99-121">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="89e99-122">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="89e99-122">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="89e99-123">Interface **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="89e99-123">An **IDispatch** interface.</span></span>|

<span data-ttu-id="89e99-124">L’exemple suivant montre la définition d’interface managée de `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="89e99-124">The following example shows the managed interface definition for `MarshalObject`.</span></span>

```vb
Interface MarshalObject
   Sub SetVariant(o As Object)
   Sub SetVariantRef(ByRef o As Object)
   Function GetVariant() As Object

   Sub SetIDispatch( <MarshalAs(UnmanagedType.IDispatch)> o As Object)
   Sub SetIDispatchRef(ByRef <MarshalAs(UnmanagedType.IDispatch)> o _
      As Object)
   Function GetIDispatch() As <MarshalAs(UnmanagedType.IDispatch)> Object
   Sub SetIUnknown( <MarshalAs(UnmanagedType.IUnknown)> o As Object)
   Sub SetIUnknownRef(ByRef <MarshalAs(UnmanagedType.IUnknown)> o _
      As Object)
   Function GetIUnknown() As <MarshalAs(UnmanagedType.IUnknown)> Object
End Interface
```

```csharp
interface MarshalObject {
   void SetVariant(Object o);
   void SetVariantRef(ref Object o);
   Object GetVariant();

   void SetIDispatch ([MarshalAs(UnmanagedType.IDispatch)]Object o);
   void SetIDispatchRef([MarshalAs(UnmanagedType.IDispatch)]ref Object o);
   [MarshalAs(UnmanagedType.IDispatch)] Object GetIDispatch();
   void SetIUnknown ([MarshalAs(UnmanagedType.IUnknown)]Object o);
   void SetIUnknownRef([MarshalAs(UnmanagedType.IUnknown)]ref Object o);
   [MarshalAs(UnmanagedType.IUnknown)] Object GetIUnknown();
}
```

<span data-ttu-id="89e99-125">Le code suivant exporte l’interface `MarshalObject` vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="89e99-125">The following code exports the `MarshalObject` interface to a type library.</span></span>

```cpp
interface MarshalObject {
   HRESULT SetVariant([in] VARIANT o);
   HRESULT SetVariantRef([in,out] VARIANT *o);
   HRESULT GetVariant([out,retval] VARIANT *o)
   HRESULT SetIDispatch([in] IDispatch *o);
   HRESULT SetIDispatchRef([in,out] IDispatch **o);
   HRESULT GetIDispatch([out,retval] IDispatch **o)
   HRESULT SetIUnknown([in] IUnknown *o);
   HRESULT SetIUnknownRef([in,out] IUnknown **o);
   HRESULT GetIUnknown([out,retval] IUnknown **o)
}
```

> [!NOTE]
> <span data-ttu-id="89e99-126">Le marshaleur d’interopérabilité libère automatiquement tout objet alloué à l’intérieur du variant après l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-126">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="89e99-127">L’exemple suivant illustre un type valeur mis en forme.</span><span class="sxs-lookup"><span data-stu-id="89e99-127">The following example shows a formatted value type.</span></span>

```vb
Public Structure ObjectHolder
   Dim o1 As Object
   <MarshalAs(UnmanagedType.IDispatch)> Public o2 As Object
End Structure
```

```csharp
public struct ObjectHolder {
   Object o1;
   [MarshalAs(UnmanagedType.IDispatch)]public Object o2;
}
```

<span data-ttu-id="89e99-128">Le code suivant exporte le type mis en forme vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="89e99-128">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="89e99-129">Marshaling d’un objet vers une interface</span><span class="sxs-lookup"><span data-stu-id="89e99-129">Marshaling Object to Interface</span></span>

<span data-ttu-id="89e99-130">Quand un objet est exposé à COM en tant qu’interface, cette interface est l’interface de classe pour le type managé <xref:System.Object> (l’interface **_Object**).</span><span class="sxs-lookup"><span data-stu-id="89e99-130">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="89e99-131">Cette interface est typée en **IDispatch** tant que<xref:System.Runtime.InteropServices.UnmanagedType>IDispatch () ou **IUnknown** (**UnmanagedType. IUnknown**) dans la bibliothèque de types résultante.</span><span class="sxs-lookup"><span data-stu-id="89e99-131">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="89e99-132">Les clients COM peuvent appeler dynamiquement les membres de la classe managée ou tout membre implémenté par ses classes dérivées via l’interface **_Object**.</span><span class="sxs-lookup"><span data-stu-id="89e99-132">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="89e99-133">Le client peut également appeler **QueryInterface** pour obtenir toute autre interface explicitement implémentée par le type managé.</span><span class="sxs-lookup"><span data-stu-id="89e99-133">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="89e99-134">Marshaling d’un objet vers un variant</span><span class="sxs-lookup"><span data-stu-id="89e99-134">Marshaling Object to Variant</span></span>

<span data-ttu-id="89e99-135">Quand un objet est marshalé en variant, le type variant interne est déterminé au moment de l’exécution en fonction des règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="89e99-135">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="89e99-136">Si la référence d’objet est null (**Nothing** en Visual Basic), l’objet est marshalé en variant de type **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="89e99-136">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="89e99-137">Si l’objet est une instance d’un type énuméré dans le tableau suivant, le type variant résultant est déterminé par les règles du marshaleur et illustré dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="89e99-137">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="89e99-138">Les autres objets qui nécessitent de contrôler explicitement le comportement de marshaling peuvent implémenter l’interface <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="89e99-138">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="89e99-139">Dans ce cas, le type variant est déterminé par le code de type retourné à partir de la méthode <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89e99-139">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="89e99-140">Sinon, l’objet est marshalé en tant que variant de type **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="89e99-140">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="89e99-141">Marshaling de types système vers des variants</span><span class="sxs-lookup"><span data-stu-id="89e99-141">Marshaling System Types to Variant</span></span>

<span data-ttu-id="89e99-142">Le tableau suivant montre les types d’objets managés et leurs types variant COM correspondants.</span><span class="sxs-lookup"><span data-stu-id="89e99-142">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="89e99-143">Ces types sont convertis uniquement quand la signature de la méthode appelée est de type <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89e99-143">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="89e99-144">Type d'objet</span><span class="sxs-lookup"><span data-stu-id="89e99-144">Object type</span></span>|<span data-ttu-id="89e99-145">Type variant COM</span><span class="sxs-lookup"><span data-stu-id="89e99-145">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="89e99-146">Référence d’objet null (**Nothing** en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="89e99-146">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="89e99-147">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="89e99-147">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="89e99-148">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="89e99-148">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="89e99-149">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="89e99-149">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="89e99-150">**VT_ERROR** avec **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="89e99-150">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="89e99-151">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="89e99-151">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="89e99-152">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="89e99-152">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="89e99-153">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="89e99-153">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="89e99-154">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="89e99-154">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="89e99-155">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="89e99-155">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="89e99-156">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="89e99-156">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="89e99-157">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="89e99-157">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="89e99-158">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="89e99-158">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="89e99-159">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="89e99-159">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="89e99-160">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="89e99-160">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="89e99-161">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="89e99-161">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="89e99-162">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="89e99-162">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="89e99-163">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="89e99-163">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="89e99-164">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="89e99-164">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="89e99-165">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="89e99-165">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="89e99-166">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="89e99-166">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="89e99-167">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="89e99-167">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="89e99-168">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="89e99-168">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="89e99-169">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="89e99-169">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="89e99-170">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="89e99-170">**VT_ARRAY**</span></span>|

<span data-ttu-id="89e99-171">En utilisant l’interface `MarshalObject` définie dans l’exemple précédent, l’exemple de code suivant démontre comment passer plusieurs types de variants à un serveur COM.</span><span class="sxs-lookup"><span data-stu-id="89e99-171">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

```vb
Dim mo As New MarshalObject()
mo.SetVariant(Nothing)         ' Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value) ' Marshal as variant of type VT_NULL.
mo.SetVariant(CInt(27))        ' Marshal as variant of type VT_I2.
mo.SetVariant(CLng(27))        ' Marshal as variant of type VT_I4.
mo.SetVariant(CSng(27.0))      ' Marshal as variant of type VT_R4.
mo.SetVariant(CDbl(27.0))      ' Marshal as variant of type VT_R8.
```

```csharp
MarshalObject mo = new MarshalObject();
mo.SetVariant(null);            // Marshal as variant of type VT_EMPTY.
mo.SetVariant(System.DBNull.Value); // Marshal as variant of type VT_NULL.
mo.SetVariant((int)27);          // Marshal as variant of type VT_I2.
mo.SetVariant((long)27);          // Marshal as variant of type VT_I4.
mo.SetVariant((single)27.0);   // Marshal as variant of type VT_R4.
mo.SetVariant((double)27.0);   // Marshal as variant of type VT_R8.
```

<span data-ttu-id="89e99-172">Les types COM qui n’ont pas de types managés correspondants peuvent être marshalés à l’aide des classes wrapper comme <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper> et <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="89e99-172">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="89e99-173">L’exemple de code suivant démontre comment utiliser ces wrappers pour passer différents types de variants à un serveur COM.</span><span class="sxs-lookup"><span data-stu-id="89e99-173">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

```vb
Imports System.Runtime.InteropServices
' Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(New UnknownWrapper(inew))
' Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(New DispatchWrapper(inew))
' Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(New ErrorWrapper(&H80054002))
' Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(New CurrencyWrapper(New Decimal(5.25)))
```

```csharp
using System.Runtime.InteropServices;
// Pass inew as a variant of type VT_UNKNOWN interface.
mo.SetVariant(new UnknownWrapper(inew));
// Pass inew as a variant of type VT_DISPATCH interface.
mo.SetVariant(new DispatchWrapper(inew));
// Pass a value as a variant of type VT_ERROR interface.
mo.SetVariant(new ErrorWrapper(0x80054002));
// Pass a value as a variant of type VT_CURRENCY interface.
mo.SetVariant(new CurrencyWrapper(new Decimal(5.25)));
```

<span data-ttu-id="89e99-174">Les classes wrapper sont définies dans l’espace de noms <xref:System.Runtime.InteropServices>.</span><span class="sxs-lookup"><span data-stu-id="89e99-174">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="89e99-175">Marshaling de l’interface IConvertible vers un variant</span><span class="sxs-lookup"><span data-stu-id="89e99-175">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="89e99-176">D’autres types que ceux répertoriés dans la section précédente peuvent contrôler la manière dont ils sont marshalés en implémentant l’interface <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="89e99-176">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="89e99-177">Si l’objet implémente l’interface **IConvertible**, le type variant COM est déterminé au moment de l’exécution par la valeur de l’énumération <xref:System.TypeCode> retournée à partir de la méthode <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89e99-177">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="89e99-178">Le tableau suivant montre les valeurs possibles pour l’énumération **TypeCode** et le type variant COM correspondant pour chaque valeur.</span><span class="sxs-lookup"><span data-stu-id="89e99-178">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="89e99-179">TypeCode</span><span class="sxs-lookup"><span data-stu-id="89e99-179">TypeCode</span></span>|<span data-ttu-id="89e99-180">Type variant COM</span><span class="sxs-lookup"><span data-stu-id="89e99-180">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="89e99-181">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="89e99-181">**TypeCode.Empty**</span></span>|<span data-ttu-id="89e99-182">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="89e99-182">**VT_EMPTY**</span></span>|
|<span data-ttu-id="89e99-183">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="89e99-183">**TypeCode.Object**</span></span>|<span data-ttu-id="89e99-184">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="89e99-184">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="89e99-185">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="89e99-185">**TypeCode.DBNull**</span></span>|<span data-ttu-id="89e99-186">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="89e99-186">**VT_NULL**</span></span>|
|<span data-ttu-id="89e99-187">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="89e99-187">**TypeCode.Boolean**</span></span>|<span data-ttu-id="89e99-188">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="89e99-188">**VT_BOOL**</span></span>|
|<span data-ttu-id="89e99-189">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="89e99-189">**TypeCode.Char**</span></span>|<span data-ttu-id="89e99-190">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="89e99-190">**VT_UI2**</span></span>|
|<span data-ttu-id="89e99-191">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="89e99-191">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="89e99-192">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="89e99-192">**VT_I1**</span></span>|
|<span data-ttu-id="89e99-193">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="89e99-193">**TypeCode.Byte**</span></span>|<span data-ttu-id="89e99-194">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="89e99-194">**VT_UI1**</span></span>|
|<span data-ttu-id="89e99-195">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="89e99-195">**TypeCode.Int16**</span></span>|<span data-ttu-id="89e99-196">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="89e99-196">**VT_I2**</span></span>|
|<span data-ttu-id="89e99-197">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="89e99-197">**TypeCode.UInt16**</span></span>|<span data-ttu-id="89e99-198">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="89e99-198">**VT_UI2**</span></span>|
|<span data-ttu-id="89e99-199">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="89e99-199">**TypeCode.Int32**</span></span>|<span data-ttu-id="89e99-200">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="89e99-200">**VT_I4**</span></span>|
|<span data-ttu-id="89e99-201">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="89e99-201">**TypeCode.UInt32**</span></span>|<span data-ttu-id="89e99-202">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="89e99-202">**VT_UI4**</span></span>|
|<span data-ttu-id="89e99-203">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="89e99-203">**TypeCode.Int64**</span></span>|<span data-ttu-id="89e99-204">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="89e99-204">**VT_I8**</span></span>|
|<span data-ttu-id="89e99-205">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="89e99-205">**TypeCode.UInt64**</span></span>|<span data-ttu-id="89e99-206">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="89e99-206">**VT_UI8**</span></span>|
|<span data-ttu-id="89e99-207">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="89e99-207">**TypeCode.Single**</span></span>|<span data-ttu-id="89e99-208">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="89e99-208">**VT_R4**</span></span>|
|<span data-ttu-id="89e99-209">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="89e99-209">**TypeCode.Double**</span></span>|<span data-ttu-id="89e99-210">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="89e99-210">**VT_R8**</span></span>|
|<span data-ttu-id="89e99-211">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="89e99-211">**TypeCode.Decimal**</span></span>|<span data-ttu-id="89e99-212">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="89e99-212">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="89e99-213">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="89e99-213">**TypeCode.DateTime**</span></span>|<span data-ttu-id="89e99-214">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="89e99-214">**VT_DATE**</span></span>|
|<span data-ttu-id="89e99-215">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="89e99-215">**TypeCode.String**</span></span>|<span data-ttu-id="89e99-216">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="89e99-216">**VT_BSTR**</span></span>|
|<span data-ttu-id="89e99-217">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-217">Not supported.</span></span>|<span data-ttu-id="89e99-218">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="89e99-218">**VT_INT**</span></span>|
|<span data-ttu-id="89e99-219">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-219">Not supported.</span></span>|<span data-ttu-id="89e99-220">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="89e99-220">**VT_UINT**</span></span>|
|<span data-ttu-id="89e99-221">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-221">Not supported.</span></span>|<span data-ttu-id="89e99-222">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="89e99-222">**VT_ARRAY**</span></span>|
|<span data-ttu-id="89e99-223">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-223">Not supported.</span></span>|<span data-ttu-id="89e99-224">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="89e99-224">**VT_RECORD**</span></span>|
|<span data-ttu-id="89e99-225">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-225">Not supported.</span></span>|<span data-ttu-id="89e99-226">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="89e99-226">**VT_CY**</span></span>|
|<span data-ttu-id="89e99-227">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-227">Not supported.</span></span>|<span data-ttu-id="89e99-228">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="89e99-228">**VT_VARIANT**</span></span>|

<span data-ttu-id="89e99-229">La valeur du variant COM est déterminée en appelant l’interface **IConvertible.To** *Type*, où **To** *Type* est la routine de conversion qui correspond au type retourné par **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="89e99-229">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="89e99-230">Par exemple, un objet qui retourne **TypeCode.Double** depuis **IConvertible.GetTypeCode** est marshalé en tant que variant COM de type **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="89e99-230">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="89e99-231">Vous pouvez obtenir la valeur du variant (stockée dans le champ **dblVal** du variant COM) en effectuant un cast en une interface **IConvertible** et en appelant la méthode <xref:System.IConvertible.ToDouble%2A>.</span><span class="sxs-lookup"><span data-stu-id="89e99-231">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="89e99-232">Marshaling d’un variant vers un objet</span><span class="sxs-lookup"><span data-stu-id="89e99-232">Marshaling Variant to Object</span></span>

<span data-ttu-id="89e99-233">Lors du marshaling d’un variant vers un objet, le type, et parfois la valeur, du variant marshalé détermine le type d’objet produit.</span><span class="sxs-lookup"><span data-stu-id="89e99-233">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="89e99-234">Le tableau suivant identifie chaque type variant et le type d’objet correspondant que le marshaleur crée quand un variant est passé de COM au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89e99-234">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="89e99-235">Type variant COM</span><span class="sxs-lookup"><span data-stu-id="89e99-235">COM variant type</span></span>|<span data-ttu-id="89e99-236">Type d'objet</span><span class="sxs-lookup"><span data-stu-id="89e99-236">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="89e99-237">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="89e99-237">**VT_EMPTY**</span></span>|<span data-ttu-id="89e99-238">Référence d’objet null (**Nothing** en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="89e99-238">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="89e99-239">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="89e99-239">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-240">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="89e99-240">**VT_DISPATCH**</span></span>|<span data-ttu-id="89e99-241">**System.__ComObject** ou null si (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="89e99-241">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="89e99-242">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="89e99-242">**VT_UNKNOWN**</span></span>|<span data-ttu-id="89e99-243">**System.__ComObject** ou null si (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="89e99-243">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="89e99-244">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="89e99-244">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-245">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="89e99-245">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-246">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="89e99-246">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-247">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="89e99-247">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-248">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="89e99-248">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-249">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="89e99-249">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-250">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="89e99-250">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-251">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="89e99-251">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-252">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="89e99-252">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-253">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="89e99-253">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-254">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="89e99-254">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-255">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="89e99-255">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-256">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="89e99-256">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-257">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="89e99-257">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-258">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="89e99-258">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-259">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="89e99-259">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-260">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="89e99-260">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-261">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="89e99-261">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-262">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="89e99-262">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="89e99-263">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="89e99-263">**VT_RECORD**</span></span>|<span data-ttu-id="89e99-264">Type valeur boxed correspondant.</span><span class="sxs-lookup"><span data-stu-id="89e99-264">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="89e99-265">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="89e99-265">**VT_VARIANT**</span></span>|<span data-ttu-id="89e99-266">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="89e99-266">Not supported.</span></span>|

<span data-ttu-id="89e99-267">Les types variant passés à partir de COM vers le code managé, puis repassés à COM peuvent ne pas conserver le même type variant durant la durée de l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-267">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="89e99-268">Envisagez ce qui se passe quand un variant de type **VT_DISPATCH** est passé à partir de COM vers le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="89e99-268">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="89e99-269">Lors du marshaling, le variant est converti en <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89e99-269">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="89e99-270">Si **Object** est ensuite repassé à COM, il est remarshalé vers un variant de type **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="89e99-270">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="89e99-271">Rien ne garantit que le variant produit quand un objet est marshalé à partir de code managé vers COM sera du même type que le variant utilisé à l’origine pour produire l’objet.</span><span class="sxs-lookup"><span data-stu-id="89e99-271">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="89e99-272">Marshaling des variants ByRef</span><span class="sxs-lookup"><span data-stu-id="89e99-272">Marshaling ByRef Variants</span></span>

<span data-ttu-id="89e99-273">Bien que les variants puissent eux-mêmes être passés par valeur ou par référence, l’indicateur **VT_BYREF** peut être également utilisé avec n’importe quel type de variant pour indiquer que le contenu du variant est passé par référence plutôt que par valeur.</span><span class="sxs-lookup"><span data-stu-id="89e99-273">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="89e99-274">La différence entre le marshaling de variants par référence et le marshaling d’un variant dont l’indicateur **VT_BYREF** est défini peut prêter à confusion.</span><span class="sxs-lookup"><span data-stu-id="89e99-274">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="89e99-275">L’illustration suivante clarifie ces différences :</span><span class="sxs-lookup"><span data-stu-id="89e99-275">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="89e99-276">![Diagramme illustrant une variante transmise à la pile.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="89e99-276">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="89e99-277">Variants passés par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="89e99-277">Variants passed by value and by reference</span></span>

<span data-ttu-id="89e99-278">**Comportement par défaut de marshaling d’objets et de variants par valeur**</span><span class="sxs-lookup"><span data-stu-id="89e99-278">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="89e99-279">Lors du passage d’objets à partir de code managé vers COM, le contenu de l’objet est copié dans un nouveau variant créé par le marshaleur à l’aide des règles définies dans [Marshaling d’un objet vers un variant](#marshaling-object-to-variant).</span><span class="sxs-lookup"><span data-stu-id="89e99-279">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="89e99-280">Les changements apportés au variant côté non managé ne sont pas retournés vers l’objet d’origine au retour de l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-280">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="89e99-281">Lors du passage de variants à partir de COM vers du code managé, le contenu du variant est copié dans un objet nouvellement créé à l’aide des règles définies dans [Marshaling d’un variant vers un objet](#marshaling-variant-to-object).</span><span class="sxs-lookup"><span data-stu-id="89e99-281">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="89e99-282">Les changements apportés à l’objet côté managé ne sont pas retournés vers le variant d’origine au retour de l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-282">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="89e99-283">**Comportement par défaut de marshaling d’objets et de variants par référence**</span><span class="sxs-lookup"><span data-stu-id="89e99-283">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="89e99-284">Pour retourner des changements à l’appelant, les paramètres doivent être passés par référence.</span><span class="sxs-lookup"><span data-stu-id="89e99-284">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="89e99-285">Par exemple, vous pouvez utiliser le mot clé **ref** en C# (ou **ByRef** en code managé Visual Basic) pour passer des paramètres par référence.</span><span class="sxs-lookup"><span data-stu-id="89e99-285">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="89e99-286">Dans COM, les paramètres de référence sont passés à l’aide d’un pointeur tel que **variant \***.</span><span class="sxs-lookup"><span data-stu-id="89e99-286">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="89e99-287">Lors du passage d’un objet à COM par référence, le marshaleur crée un variant et copie le contenu de la référence d’objet dans le variant avant que l’appel ne soit effectué.</span><span class="sxs-lookup"><span data-stu-id="89e99-287">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="89e99-288">Le variant est passé à la fonction non managée où l’utilisateur est libre de changer le contenu du variant.</span><span class="sxs-lookup"><span data-stu-id="89e99-288">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="89e99-289">Au retour de l’appel, tout changement apporté au variant côté non managé est retourné vers l’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="89e99-289">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="89e99-290">Si le type de variant est différent du type du variant passé à l’appel, les changements sont retournés à un objet d’un type différent.</span><span class="sxs-lookup"><span data-stu-id="89e99-290">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="89e99-291">Cela signifie que le type de l’objet passé dans l’appel peut être différent du type de l’objet retourné à partir de l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-291">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="89e99-292">Lors du passage d’un variant au code managé par référence, le marshaleur crée un objet et copie le contenu du variant dans l’objet avant que l’appel ne soit effectué.</span><span class="sxs-lookup"><span data-stu-id="89e99-292">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="89e99-293">Une référence à l’objet est passée à la fonction managée, où l’utilisateur est libre de changer l’objet.</span><span class="sxs-lookup"><span data-stu-id="89e99-293">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="89e99-294">Au retour de l’appel, tout changement apporté à l’objet référencé est retourné vers le variant d’origine.</span><span class="sxs-lookup"><span data-stu-id="89e99-294">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="89e99-295">Si le type de l’objet est différent du type de l’objet passé dans l’appel, le type du variant d’origine est changé et la valeur est retournée dans le variant.</span><span class="sxs-lookup"><span data-stu-id="89e99-295">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="89e99-296">Là encore, le type du variant passé dans l’appel peut être différent du type du variant retourné à partir de l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-296">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="89e99-297">**Comportement par défaut de marshaling d’un variant dont l’indicateur VT_BYREF est défini**</span><span class="sxs-lookup"><span data-stu-id="89e99-297">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="89e99-298">Un variant passé à du code managé par valeur peut avoir l’indicateur **VT_BYREF** défini pour indiquer que le variant contient une référence plutôt qu’une valeur.</span><span class="sxs-lookup"><span data-stu-id="89e99-298">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="89e99-299">Dans ce cas, le variant est toujours marshalé vers un objet, car le variant est passé par valeur.</span><span class="sxs-lookup"><span data-stu-id="89e99-299">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="89e99-300">Le marshaleur déréférence automatiquement le contenu du variant et le copie dans un objet nouvellement créé avant d’effectuer l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-300">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="89e99-301">L’objet est ensuite passé à la fonction managée ; cependant, au retour de l’appel, l’objet n’est pas retourné dans le variant d’origine.</span><span class="sxs-lookup"><span data-stu-id="89e99-301">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="89e99-302">Les changements apportés à l’objet managé sont perdus.</span><span class="sxs-lookup"><span data-stu-id="89e99-302">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="89e99-303">Il est impossible de changer la valeur d’un variant passé par valeur, même si l’indicateur **VT_BYREF** de ce variant est défini.</span><span class="sxs-lookup"><span data-stu-id="89e99-303">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="89e99-304">Un variant passé à du code managé par référence peut aussi avoir l’indicateur **VT_BYREF** défini pour indiquer que le variant contient une autre référence.</span><span class="sxs-lookup"><span data-stu-id="89e99-304">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="89e99-305">Si c’est le cas, le variant est marshalé vers un objet **ref** parce qu’il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="89e99-305">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="89e99-306">Le marshaleur déréférence automatiquement le contenu du variant et le copie dans un objet nouvellement créé avant d’effectuer l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-306">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="89e99-307">Au retour de l’appel, la valeur de l’objet est retournée vers la référence située dans le variant d’origine uniquement si l’objet est du même type que l’objet passé.</span><span class="sxs-lookup"><span data-stu-id="89e99-307">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="89e99-308">Autrement dit, la propagation ne change pas le type d’un variant avec l’indicateur **VT_BYREF** défini.</span><span class="sxs-lookup"><span data-stu-id="89e99-308">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="89e99-309">Si le type de l’objet est modifié durant l’appel, une exception <xref:System.InvalidCastException> se produit au retour de l’appel.</span><span class="sxs-lookup"><span data-stu-id="89e99-309">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="89e99-310">Le tableau suivant résume les règles de propagation pour les variants et les objets.</span><span class="sxs-lookup"><span data-stu-id="89e99-310">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="89e99-311">À partir</span><span class="sxs-lookup"><span data-stu-id="89e99-311">From</span></span>|<span data-ttu-id="89e99-312">À</span><span class="sxs-lookup"><span data-stu-id="89e99-312">To</span></span>|<span data-ttu-id="89e99-313">Changements retournés</span><span class="sxs-lookup"><span data-stu-id="89e99-313">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="89e99-314">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="89e99-314">**Variant**  *v*</span></span>|<span data-ttu-id="89e99-315">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="89e99-315">**Object**  *o*</span></span>|<span data-ttu-id="89e99-316">Jamais</span><span class="sxs-lookup"><span data-stu-id="89e99-316">Never</span></span>|
|<span data-ttu-id="89e99-317">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="89e99-317">**Object**  *o*</span></span>|<span data-ttu-id="89e99-318">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="89e99-318">**Variant**  *v*</span></span>|<span data-ttu-id="89e99-319">Jamais</span><span class="sxs-lookup"><span data-stu-id="89e99-319">Never</span></span>|
|<span data-ttu-id="89e99-320">**Variante**   ***\****  *PV*</span><span class="sxs-lookup"><span data-stu-id="89e99-320">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="89e99-321">**Ref Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="89e99-321">**Ref Object**  *o*</span></span>|<span data-ttu-id="89e99-322">Toujours</span><span class="sxs-lookup"><span data-stu-id="89e99-322">Always</span></span>|
|<span data-ttu-id="89e99-323">**Objet Ref**  *o*</span><span class="sxs-lookup"><span data-stu-id="89e99-323">**Ref object**  *o*</span></span>|<span data-ttu-id="89e99-324">**Variante**   ***\****  *PV*</span><span class="sxs-lookup"><span data-stu-id="89e99-324">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="89e99-325">Toujours</span><span class="sxs-lookup"><span data-stu-id="89e99-325">Always</span></span>|
|<span data-ttu-id="89e99-326">**Variante**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span><span class="sxs-lookup"><span data-stu-id="89e99-326">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="89e99-327">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="89e99-327">**Object**  *o*</span></span>|<span data-ttu-id="89e99-328">Jamais</span><span class="sxs-lookup"><span data-stu-id="89e99-328">Never</span></span>|
|<span data-ttu-id="89e99-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="89e99-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="89e99-330">**Ref Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="89e99-330">**Ref Object**  *o*</span></span>|<span data-ttu-id="89e99-331">Uniquement si le type n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="89e99-331">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="89e99-332">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89e99-332">See also</span></span>

- [<span data-ttu-id="89e99-333">comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="89e99-333">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="89e99-334">Types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="89e99-334">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="89e99-335">[Attributs directionnels](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="89e99-335">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="89e99-336">copie et épinglage</span><span class="sxs-lookup"><span data-stu-id="89e99-336">Copying and Pinning</span></span>](copying-and-pinning.md)
