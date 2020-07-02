---
title: Marshaling par défaut pour les objets
description: Comprendre le marshaling par défaut pour les objets. Passez en revue les options de marshaling. Marshaler des objets vers des interfaces ou des variantes, des variantes vers des objets et des variantes ByRef.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- objects, interop marshaling
- interop marshaling, objects
ms.assetid: c2ef0284-b061-4e12-b6d3-6a502b9cc558
ms.openlocfilehash: 7b8f94f4dfd8e8b9e8e04df8de5f8266a8581a92
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618450"
---
# <a name="default-marshaling-for-objects"></a><span data-ttu-id="13e82-105">Marshaling par défaut pour les objets</span><span class="sxs-lookup"><span data-stu-id="13e82-105">Default Marshaling for Objects</span></span>

<span data-ttu-id="13e82-106">Les paramètres et les champs de type <xref:System.Object?displayProperty=nameWithType> peuvent être exposés à un code non managé sous la forme de l’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="13e82-106">Parameters and fields typed as <xref:System.Object?displayProperty=nameWithType> can be exposed to unmanaged code as one of the following types:</span></span>

- <span data-ttu-id="13e82-107">Un variant quand l’objet est un paramètre.</span><span class="sxs-lookup"><span data-stu-id="13e82-107">A variant when the object is a parameter.</span></span>

- <span data-ttu-id="13e82-108">Une interface quand l’objet est un champ de structure.</span><span class="sxs-lookup"><span data-stu-id="13e82-108">An interface when the object is a structure field.</span></span>

<span data-ttu-id="13e82-109">Seul COM interop prend en charge le marshaling des types d’objets.</span><span class="sxs-lookup"><span data-stu-id="13e82-109">Only COM interop supports marshaling for object types.</span></span> <span data-ttu-id="13e82-110">Le comportement par défaut est de marshaler des objets vers des variants COM.</span><span class="sxs-lookup"><span data-stu-id="13e82-110">The default behavior is to marshal objects to COM variants.</span></span> <span data-ttu-id="13e82-111">Ces règles s’appliquent uniquement au type **Object** et ne s’appliquent pas aux objets fortement typés issus de la classe **Object**.</span><span class="sxs-lookup"><span data-stu-id="13e82-111">These rules apply only to the type **Object** and do not apply to strongly typed objects that derive from the **Object** class.</span></span>

## <a name="marshaling-options"></a><span data-ttu-id="13e82-112">Options de marshaling</span><span class="sxs-lookup"><span data-stu-id="13e82-112">Marshaling Options</span></span>

<span data-ttu-id="13e82-113">Le tableau suivant montre les options de marshaling pour le type de données **Object**.</span><span class="sxs-lookup"><span data-stu-id="13e82-113">The following table shows the marshaling options for the **Object** data type.</span></span> <span data-ttu-id="13e82-114">L’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d’énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler des objets.</span><span class="sxs-lookup"><span data-stu-id="13e82-114">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal objects.</span></span>

|<span data-ttu-id="13e82-115">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="13e82-115">Enumeration type</span></span>|<span data-ttu-id="13e82-116">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="13e82-116">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="13e82-117">**UnmanagedType.Struct**</span><span class="sxs-lookup"><span data-stu-id="13e82-117">**UnmanagedType.Struct**</span></span><br /><br /> <span data-ttu-id="13e82-118">(valeur par défaut des paramètres)</span><span class="sxs-lookup"><span data-stu-id="13e82-118">(default for parameters)</span></span>|<span data-ttu-id="13e82-119">Variant de style COM.</span><span class="sxs-lookup"><span data-stu-id="13e82-119">A COM-style variant.</span></span>|
|<span data-ttu-id="13e82-120">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="13e82-120">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="13e82-121">Interface **IDispatch**, si possible ; sinon, interface **IUnknown**.</span><span class="sxs-lookup"><span data-stu-id="13e82-121">An **IDispatch** interface, if possible; otherwise, an **IUnknown** interface.</span></span>|
|<span data-ttu-id="13e82-122">**UnmanagedType.IUnknown**</span><span class="sxs-lookup"><span data-stu-id="13e82-122">**UnmanagedType.IUnknown**</span></span><br /><br /> <span data-ttu-id="13e82-123">(valeur par défaut des champs)</span><span class="sxs-lookup"><span data-stu-id="13e82-123">(default for fields)</span></span>|<span data-ttu-id="13e82-124">Interface **IUnknown**.</span><span class="sxs-lookup"><span data-stu-id="13e82-124">An **IUnknown** interface.</span></span>|
|<span data-ttu-id="13e82-125">**UnmanagedType.IDispatch**</span><span class="sxs-lookup"><span data-stu-id="13e82-125">**UnmanagedType.IDispatch**</span></span>|<span data-ttu-id="13e82-126">Interface **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="13e82-126">An **IDispatch** interface.</span></span>|

<span data-ttu-id="13e82-127">L’exemple suivant montre la définition d’interface managée de `MarshalObject`.</span><span class="sxs-lookup"><span data-stu-id="13e82-127">The following example shows the managed interface definition for `MarshalObject`.</span></span>

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

<span data-ttu-id="13e82-128">Le code suivant exporte l’interface `MarshalObject` vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="13e82-128">The following code exports the `MarshalObject` interface to a type library.</span></span>

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
> <span data-ttu-id="13e82-129">Le marshaleur d’interopérabilité libère automatiquement tout objet alloué à l’intérieur du variant après l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-129">The interop marshaler automatically frees any allocated object inside the variant after the call.</span></span>

<span data-ttu-id="13e82-130">L’exemple suivant illustre un type valeur mis en forme.</span><span class="sxs-lookup"><span data-stu-id="13e82-130">The following example shows a formatted value type.</span></span>

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

<span data-ttu-id="13e82-131">Le code suivant exporte le type mis en forme vers une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="13e82-131">The following code exports the formatted type to a type library.</span></span>

```cpp
struct ObjectHolder {
   VARIANT o1;
   IDispatch *o2;
}
```

## <a name="marshaling-object-to-interface"></a><span data-ttu-id="13e82-132">Marshaling d’un objet vers une interface</span><span class="sxs-lookup"><span data-stu-id="13e82-132">Marshaling Object to Interface</span></span>

<span data-ttu-id="13e82-133">Quand un objet est exposé à COM en tant qu’interface, cette interface est l’interface de classe pour le type managé <xref:System.Object> (l’interface **_Object**).</span><span class="sxs-lookup"><span data-stu-id="13e82-133">When an object is exposed to COM as an interface, that interface is the class interface for the managed type <xref:System.Object> (the **_Object** interface).</span></span> <span data-ttu-id="13e82-134">Cette interface est typée en tant que **IDispatch** ( <xref:System.Runtime.InteropServices.UnmanagedType> ) ou **IUnknown** (**UnmanagedType. IUnknown**) dans la bibliothèque de types résultante.</span><span class="sxs-lookup"><span data-stu-id="13e82-134">This interface is typed as an **IDispatch** (<xref:System.Runtime.InteropServices.UnmanagedType>) or an **IUnknown** (**UnmanagedType.IUnknown**) in the resulting type library.</span></span> <span data-ttu-id="13e82-135">Les clients COM peuvent appeler dynamiquement les membres de la classe managée ou tout membre implémenté par ses classes dérivées via l’interface **_Object**.</span><span class="sxs-lookup"><span data-stu-id="13e82-135">COM clients can dynamically invoke the members of the managed class or any members implemented by its derived classes through the **_Object** interface.</span></span> <span data-ttu-id="13e82-136">Le client peut également appeler **QueryInterface** pour obtenir toute autre interface explicitement implémentée par le type managé.</span><span class="sxs-lookup"><span data-stu-id="13e82-136">The client can also call **QueryInterface** to obtain any other interface explicitly implemented by the managed type.</span></span>

## <a name="marshaling-object-to-variant"></a><span data-ttu-id="13e82-137">Marshaling d’un objet vers un variant</span><span class="sxs-lookup"><span data-stu-id="13e82-137">Marshaling Object to Variant</span></span>

<span data-ttu-id="13e82-138">Quand un objet est marshalé en variant, le type variant interne est déterminé au moment de l’exécution en fonction des règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="13e82-138">When an object is marshaled to a variant, the internal variant type is determined at run time, based on the following rules:</span></span>

- <span data-ttu-id="13e82-139">Si la référence d’objet est null (**Nothing** en Visual Basic), l’objet est marshalé en variant de type **VT_EMPTY**.</span><span class="sxs-lookup"><span data-stu-id="13e82-139">If the object reference is null (**Nothing** in Visual Basic), the object is marshaled to a variant of type **VT_EMPTY**.</span></span>

- <span data-ttu-id="13e82-140">Si l’objet est une instance d’un type énuméré dans le tableau suivant, le type variant résultant est déterminé par les règles du marshaleur et illustré dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="13e82-140">If the object is an instance of any type listed in the following table, the resulting variant type is determined by the rules built into the marshaler and shown in the table.</span></span>

- <span data-ttu-id="13e82-141">Les autres objets qui nécessitent de contrôler explicitement le comportement de marshaling peuvent implémenter l’interface <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="13e82-141">Other objects that need to explicitly control the marshaling behavior can implement the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="13e82-142">Dans ce cas, le type variant est déterminé par le code de type retourné à partir de la méthode <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13e82-142">In that case, the variant type is determined by the type code returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="13e82-143">Sinon, l’objet est marshalé en tant que variant de type **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="13e82-143">Otherwise, the object is marshaled as a variant of type **VT_UNKNOWN**.</span></span>

### <a name="marshaling-system-types-to-variant"></a><span data-ttu-id="13e82-144">Marshaling de types système vers des variants</span><span class="sxs-lookup"><span data-stu-id="13e82-144">Marshaling System Types to Variant</span></span>

<span data-ttu-id="13e82-145">Le tableau suivant montre les types d’objets managés et leurs types variant COM correspondants.</span><span class="sxs-lookup"><span data-stu-id="13e82-145">The following table shows managed object types and their corresponding COM variant types.</span></span> <span data-ttu-id="13e82-146">Ces types sont convertis uniquement quand la signature de la méthode appelée est de type <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13e82-146">These types are converted only when the signature of the method being called is of type <xref:System.Object?displayProperty=nameWithType>.</span></span>

|<span data-ttu-id="13e82-147">Type d'objet</span><span class="sxs-lookup"><span data-stu-id="13e82-147">Object type</span></span>|<span data-ttu-id="13e82-148">Type variant COM</span><span class="sxs-lookup"><span data-stu-id="13e82-148">COM variant type</span></span>|
|-----------------|----------------------|
|<span data-ttu-id="13e82-149">Référence d’objet null (**Nothing** en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="13e82-149">Null object reference (**Nothing** in Visual Basic).</span></span>|<span data-ttu-id="13e82-150">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="13e82-150">**VT_EMPTY**</span></span>|
|<xref:System.DBNull?displayProperty=nameWithType>|<span data-ttu-id="13e82-151">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="13e82-151">**VT_NULL**</span></span>|
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|<span data-ttu-id="13e82-152">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="13e82-152">**VT_ERROR**</span></span>|
|<xref:System.Reflection.Missing?displayProperty=nameWithType>|<span data-ttu-id="13e82-153">**VT_ERROR** avec **E_PARAMNOTFOUND**</span><span class="sxs-lookup"><span data-stu-id="13e82-153">**VT_ERROR** with **E_PARAMNOTFOUND**</span></span>|
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|<span data-ttu-id="13e82-154">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="13e82-154">**VT_DISPATCH**</span></span>|
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|<span data-ttu-id="13e82-155">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="13e82-155">**VT_UNKNOWN**</span></span>|
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|<span data-ttu-id="13e82-156">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="13e82-156">**VT_CY**</span></span>|
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="13e82-157">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="13e82-157">**VT_BOOL**</span></span>|
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="13e82-158">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="13e82-158">**VT_I1**</span></span>|
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="13e82-159">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="13e82-159">**VT_UI1**</span></span>|
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="13e82-160">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="13e82-160">**VT_I2**</span></span>|
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="13e82-161">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="13e82-161">**VT_UI2**</span></span>|
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="13e82-162">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="13e82-162">**VT_I4**</span></span>|
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="13e82-163">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="13e82-163">**VT_UI4**</span></span>|
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="13e82-164">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="13e82-164">**VT_I8**</span></span>|
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="13e82-165">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="13e82-165">**VT_UI8**</span></span>|
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="13e82-166">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="13e82-166">**VT_R4**</span></span>|
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="13e82-167">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="13e82-167">**VT_R8**</span></span>|
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="13e82-168">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="13e82-168">**VT_DECIMAL**</span></span>|
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="13e82-169">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="13e82-169">**VT_DATE**</span></span>|
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="13e82-170">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="13e82-170">**VT_BSTR**</span></span>|
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="13e82-171">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="13e82-171">**VT_INT**</span></span>|
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="13e82-172">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="13e82-172">**VT_UINT**</span></span>|
|<xref:System.Array?displayProperty=nameWithType>|<span data-ttu-id="13e82-173">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="13e82-173">**VT_ARRAY**</span></span>|

<span data-ttu-id="13e82-174">En utilisant l’interface `MarshalObject` définie dans l’exemple précédent, l’exemple de code suivant démontre comment passer plusieurs types de variants à un serveur COM.</span><span class="sxs-lookup"><span data-stu-id="13e82-174">Using the `MarshalObject` interface defined in the previous example, the following code example demonstrates how to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="13e82-175">Les types COM qui n’ont pas de types managés correspondants peuvent être marshalés à l’aide des classes wrapper comme <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper> et <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span><span class="sxs-lookup"><span data-stu-id="13e82-175">COM types that do not have corresponding managed types can be marshaled using wrapper classes such as <xref:System.Runtime.InteropServices.ErrorWrapper>, <xref:System.Runtime.InteropServices.DispatchWrapper>, <xref:System.Runtime.InteropServices.UnknownWrapper>, and <xref:System.Runtime.InteropServices.CurrencyWrapper>.</span></span> <span data-ttu-id="13e82-176">L’exemple de code suivant démontre comment utiliser ces wrappers pour passer différents types de variants à un serveur COM.</span><span class="sxs-lookup"><span data-stu-id="13e82-176">The following code example demonstrates how to use these wrappers to pass various types of variants to a COM server.</span></span>

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

<span data-ttu-id="13e82-177">Les classes wrapper sont définies dans l’espace de noms <xref:System.Runtime.InteropServices>.</span><span class="sxs-lookup"><span data-stu-id="13e82-177">The wrapper classes are defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>

### <a name="marshaling-the-iconvertible-interface-to-variant"></a><span data-ttu-id="13e82-178">Marshaling de l’interface IConvertible vers un variant</span><span class="sxs-lookup"><span data-stu-id="13e82-178">Marshaling the IConvertible Interface to Variant</span></span>

<span data-ttu-id="13e82-179">D’autres types que ceux répertoriés dans la section précédente peuvent contrôler la manière dont ils sont marshalés en implémentant l’interface <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="13e82-179">Types other than those listed in the previous section can control how they are marshaled by implementing the <xref:System.IConvertible> interface.</span></span> <span data-ttu-id="13e82-180">Si l’objet implémente l’interface **IConvertible**, le type variant COM est déterminé au moment de l’exécution par la valeur de l’énumération <xref:System.TypeCode> retournée à partir de la méthode <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13e82-180">If the object implements the **IConvertible** interface, the COM variant type is determined at run time by the value of the <xref:System.TypeCode> enumeration returned from the <xref:System.IConvertible.GetTypeCode%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="13e82-181">Le tableau suivant montre les valeurs possibles pour l’énumération **TypeCode** et le type variant COM correspondant pour chaque valeur.</span><span class="sxs-lookup"><span data-stu-id="13e82-181">The following table shows the possible values for the **TypeCode** enumeration and the corresponding COM variant type for each value.</span></span>

|<span data-ttu-id="13e82-182">TypeCode</span><span class="sxs-lookup"><span data-stu-id="13e82-182">TypeCode</span></span>|<span data-ttu-id="13e82-183">Type variant COM</span><span class="sxs-lookup"><span data-stu-id="13e82-183">COM variant type</span></span>|
|--------------|----------------------|
|<span data-ttu-id="13e82-184">**TypeCode.Empty**</span><span class="sxs-lookup"><span data-stu-id="13e82-184">**TypeCode.Empty**</span></span>|<span data-ttu-id="13e82-185">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="13e82-185">**VT_EMPTY**</span></span>|
|<span data-ttu-id="13e82-186">**TypeCode.Object**</span><span class="sxs-lookup"><span data-stu-id="13e82-186">**TypeCode.Object**</span></span>|<span data-ttu-id="13e82-187">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="13e82-187">**VT_UNKNOWN**</span></span>|
|<span data-ttu-id="13e82-188">**TypeCode.DBNull**</span><span class="sxs-lookup"><span data-stu-id="13e82-188">**TypeCode.DBNull**</span></span>|<span data-ttu-id="13e82-189">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="13e82-189">**VT_NULL**</span></span>|
|<span data-ttu-id="13e82-190">**TypeCode.Boolean**</span><span class="sxs-lookup"><span data-stu-id="13e82-190">**TypeCode.Boolean**</span></span>|<span data-ttu-id="13e82-191">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="13e82-191">**VT_BOOL**</span></span>|
|<span data-ttu-id="13e82-192">**TypeCode.Char**</span><span class="sxs-lookup"><span data-stu-id="13e82-192">**TypeCode.Char**</span></span>|<span data-ttu-id="13e82-193">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="13e82-193">**VT_UI2**</span></span>|
|<span data-ttu-id="13e82-194">**TypeCode.Sbyte**</span><span class="sxs-lookup"><span data-stu-id="13e82-194">**TypeCode.Sbyte**</span></span>|<span data-ttu-id="13e82-195">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="13e82-195">**VT_I1**</span></span>|
|<span data-ttu-id="13e82-196">**TypeCode.Byte**</span><span class="sxs-lookup"><span data-stu-id="13e82-196">**TypeCode.Byte**</span></span>|<span data-ttu-id="13e82-197">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="13e82-197">**VT_UI1**</span></span>|
|<span data-ttu-id="13e82-198">**TypeCode.Int16**</span><span class="sxs-lookup"><span data-stu-id="13e82-198">**TypeCode.Int16**</span></span>|<span data-ttu-id="13e82-199">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="13e82-199">**VT_I2**</span></span>|
|<span data-ttu-id="13e82-200">**TypeCode.UInt16**</span><span class="sxs-lookup"><span data-stu-id="13e82-200">**TypeCode.UInt16**</span></span>|<span data-ttu-id="13e82-201">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="13e82-201">**VT_UI2**</span></span>|
|<span data-ttu-id="13e82-202">**TypeCode.Int32**</span><span class="sxs-lookup"><span data-stu-id="13e82-202">**TypeCode.Int32**</span></span>|<span data-ttu-id="13e82-203">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="13e82-203">**VT_I4**</span></span>|
|<span data-ttu-id="13e82-204">**TypeCode.UInt32**</span><span class="sxs-lookup"><span data-stu-id="13e82-204">**TypeCode.UInt32**</span></span>|<span data-ttu-id="13e82-205">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="13e82-205">**VT_UI4**</span></span>|
|<span data-ttu-id="13e82-206">**TypeCode.Int64**</span><span class="sxs-lookup"><span data-stu-id="13e82-206">**TypeCode.Int64**</span></span>|<span data-ttu-id="13e82-207">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="13e82-207">**VT_I8**</span></span>|
|<span data-ttu-id="13e82-208">**TypeCode.UInt64**</span><span class="sxs-lookup"><span data-stu-id="13e82-208">**TypeCode.UInt64**</span></span>|<span data-ttu-id="13e82-209">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="13e82-209">**VT_UI8**</span></span>|
|<span data-ttu-id="13e82-210">**TypeCode.Single**</span><span class="sxs-lookup"><span data-stu-id="13e82-210">**TypeCode.Single**</span></span>|<span data-ttu-id="13e82-211">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="13e82-211">**VT_R4**</span></span>|
|<span data-ttu-id="13e82-212">**TypeCode.Double**</span><span class="sxs-lookup"><span data-stu-id="13e82-212">**TypeCode.Double**</span></span>|<span data-ttu-id="13e82-213">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="13e82-213">**VT_R8**</span></span>|
|<span data-ttu-id="13e82-214">**TypeCode.Decimal**</span><span class="sxs-lookup"><span data-stu-id="13e82-214">**TypeCode.Decimal**</span></span>|<span data-ttu-id="13e82-215">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="13e82-215">**VT_DECIMAL**</span></span>|
|<span data-ttu-id="13e82-216">**TypeCode.DateTime**</span><span class="sxs-lookup"><span data-stu-id="13e82-216">**TypeCode.DateTime**</span></span>|<span data-ttu-id="13e82-217">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="13e82-217">**VT_DATE**</span></span>|
|<span data-ttu-id="13e82-218">**TypeCode.String**</span><span class="sxs-lookup"><span data-stu-id="13e82-218">**TypeCode.String**</span></span>|<span data-ttu-id="13e82-219">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="13e82-219">**VT_BSTR**</span></span>|
|<span data-ttu-id="13e82-220">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-220">Not supported.</span></span>|<span data-ttu-id="13e82-221">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="13e82-221">**VT_INT**</span></span>|
|<span data-ttu-id="13e82-222">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-222">Not supported.</span></span>|<span data-ttu-id="13e82-223">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="13e82-223">**VT_UINT**</span></span>|
|<span data-ttu-id="13e82-224">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-224">Not supported.</span></span>|<span data-ttu-id="13e82-225">**VT_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="13e82-225">**VT_ARRAY**</span></span>|
|<span data-ttu-id="13e82-226">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-226">Not supported.</span></span>|<span data-ttu-id="13e82-227">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="13e82-227">**VT_RECORD**</span></span>|
|<span data-ttu-id="13e82-228">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-228">Not supported.</span></span>|<span data-ttu-id="13e82-229">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="13e82-229">**VT_CY**</span></span>|
|<span data-ttu-id="13e82-230">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-230">Not supported.</span></span>|<span data-ttu-id="13e82-231">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="13e82-231">**VT_VARIANT**</span></span>|

<span data-ttu-id="13e82-232">La valeur du variant COM est déterminée en appelant l’interface **IConvertible.To** *Type*, où **To** *Type* est la routine de conversion qui correspond au type retourné par **IConvertible.GetTypeCode**.</span><span class="sxs-lookup"><span data-stu-id="13e82-232">The value of the COM variant is determined by calling the **IConvertible.To** *Type* interface, where **To** *Type* is the conversion routine that corresponds to the type that was returned from **IConvertible.GetTypeCode**.</span></span> <span data-ttu-id="13e82-233">Par exemple, un objet qui retourne **TypeCode.Double** depuis **IConvertible.GetTypeCode** est marshalé en tant que variant COM de type **VT_R8**.</span><span class="sxs-lookup"><span data-stu-id="13e82-233">For example, an object that returns **TypeCode.Double** from **IConvertible.GetTypeCode** is marshaled as a COM variant of type **VT_R8**.</span></span> <span data-ttu-id="13e82-234">Vous pouvez obtenir la valeur du variant (stockée dans le champ **dblVal** du variant COM) en effectuant un cast en une interface **IConvertible** et en appelant la méthode <xref:System.IConvertible.ToDouble%2A>.</span><span class="sxs-lookup"><span data-stu-id="13e82-234">You can obtain the value of the variant (stored in the **dblVal** field of the COM variant) by casting to the **IConvertible** interface and calling the <xref:System.IConvertible.ToDouble%2A> method.</span></span>

## <a name="marshaling-variant-to-object"></a><span data-ttu-id="13e82-235">Marshaling d’un variant vers un objet</span><span class="sxs-lookup"><span data-stu-id="13e82-235">Marshaling Variant to Object</span></span>

<span data-ttu-id="13e82-236">Lors du marshaling d’un variant vers un objet, le type, et parfois la valeur, du variant marshalé détermine le type d’objet produit.</span><span class="sxs-lookup"><span data-stu-id="13e82-236">When marshaling a variant to an object, the type, and sometimes the value, of the marshaled variant determines the type of object produced.</span></span> <span data-ttu-id="13e82-237">Le tableau suivant identifie chaque type variant et le type d’objet correspondant que le marshaleur crée quand un variant est passé de COM au .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13e82-237">The following table identifies each variant type and the corresponding object type that the marshaler creates when a variant is passed from COM to the .NET Framework.</span></span>

|<span data-ttu-id="13e82-238">Type variant COM</span><span class="sxs-lookup"><span data-stu-id="13e82-238">COM variant type</span></span>|<span data-ttu-id="13e82-239">Type d'objet</span><span class="sxs-lookup"><span data-stu-id="13e82-239">Object type</span></span>|
|----------------------|-----------------|
|<span data-ttu-id="13e82-240">**VT_EMPTY**</span><span class="sxs-lookup"><span data-stu-id="13e82-240">**VT_EMPTY**</span></span>|<span data-ttu-id="13e82-241">Référence d’objet null (**Nothing** en Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="13e82-241">Null object reference (**Nothing** in Visual Basic).</span></span>|
|<span data-ttu-id="13e82-242">**VT_NULL**</span><span class="sxs-lookup"><span data-stu-id="13e82-242">**VT_NULL**</span></span>|<xref:System.DBNull?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-243">**VT_DISPATCH**</span><span class="sxs-lookup"><span data-stu-id="13e82-243">**VT_DISPATCH**</span></span>|<span data-ttu-id="13e82-244">**System.__ComObject** ou null si (pdispVal == null)</span><span class="sxs-lookup"><span data-stu-id="13e82-244">**System.__ComObject** or null if (pdispVal == null)</span></span>|
|<span data-ttu-id="13e82-245">**VT_UNKNOWN**</span><span class="sxs-lookup"><span data-stu-id="13e82-245">**VT_UNKNOWN**</span></span>|<span data-ttu-id="13e82-246">**System.__ComObject** ou null si (punkVal == null)</span><span class="sxs-lookup"><span data-stu-id="13e82-246">**System.__ComObject** or null if (punkVal == null)</span></span>|
|<span data-ttu-id="13e82-247">**VT_ERROR**</span><span class="sxs-lookup"><span data-stu-id="13e82-247">**VT_ERROR**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-248">**VT_BOOL**</span><span class="sxs-lookup"><span data-stu-id="13e82-248">**VT_BOOL**</span></span>|<xref:System.Boolean?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-249">**VT_I1**</span><span class="sxs-lookup"><span data-stu-id="13e82-249">**VT_I1**</span></span>|<xref:System.SByte?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-250">**VT_UI1**</span><span class="sxs-lookup"><span data-stu-id="13e82-250">**VT_UI1**</span></span>|<xref:System.Byte?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-251">**VT_I2**</span><span class="sxs-lookup"><span data-stu-id="13e82-251">**VT_I2**</span></span>|<xref:System.Int16?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-252">**VT_UI2**</span><span class="sxs-lookup"><span data-stu-id="13e82-252">**VT_UI2**</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-253">**VT_I4**</span><span class="sxs-lookup"><span data-stu-id="13e82-253">**VT_I4**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-254">**VT_UI4**</span><span class="sxs-lookup"><span data-stu-id="13e82-254">**VT_UI4**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-255">**VT_I8**</span><span class="sxs-lookup"><span data-stu-id="13e82-255">**VT_I8**</span></span>|<xref:System.Int64?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-256">**VT_UI8**</span><span class="sxs-lookup"><span data-stu-id="13e82-256">**VT_UI8**</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-257">**VT_R4**</span><span class="sxs-lookup"><span data-stu-id="13e82-257">**VT_R4**</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-258">**VT_R8**</span><span class="sxs-lookup"><span data-stu-id="13e82-258">**VT_R8**</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-259">**VT_DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="13e82-259">**VT_DECIMAL**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-260">**VT_DATE**</span><span class="sxs-lookup"><span data-stu-id="13e82-260">**VT_DATE**</span></span>|<xref:System.DateTime?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-261">**VT_BSTR**</span><span class="sxs-lookup"><span data-stu-id="13e82-261">**VT_BSTR**</span></span>|<xref:System.String?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-262">**VT_INT**</span><span class="sxs-lookup"><span data-stu-id="13e82-262">**VT_INT**</span></span>|<xref:System.Int32?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-263">**VT_UINT**</span><span class="sxs-lookup"><span data-stu-id="13e82-263">**VT_UINT**</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-264">**VT_ARRAY** &#124; **VT_**\*</span><span class="sxs-lookup"><span data-stu-id="13e82-264">**VT_ARRAY** &#124; **VT_**\*</span></span>|<xref:System.Array?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-265">**VT_CY**</span><span class="sxs-lookup"><span data-stu-id="13e82-265">**VT_CY**</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|
|<span data-ttu-id="13e82-266">**VT_RECORD**</span><span class="sxs-lookup"><span data-stu-id="13e82-266">**VT_RECORD**</span></span>|<span data-ttu-id="13e82-267">Type valeur boxed correspondant.</span><span class="sxs-lookup"><span data-stu-id="13e82-267">Corresponding boxed value type.</span></span>|
|<span data-ttu-id="13e82-268">**VT_VARIANT**</span><span class="sxs-lookup"><span data-stu-id="13e82-268">**VT_VARIANT**</span></span>|<span data-ttu-id="13e82-269">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="13e82-269">Not supported.</span></span>|

<span data-ttu-id="13e82-270">Les types variant passés à partir de COM vers le code managé, puis repassés à COM peuvent ne pas conserver le même type variant durant la durée de l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-270">Variant types passed from COM to managed code and then back to COM might not retain the same variant type for the duration of the call.</span></span> <span data-ttu-id="13e82-271">Envisagez ce qui se passe quand un variant de type **VT_DISPATCH** est passé à partir de COM vers le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13e82-271">Consider what happens when a variant of type **VT_DISPATCH** is passed from COM to the .NET Framework.</span></span> <span data-ttu-id="13e82-272">Lors du marshaling, le variant est converti en <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13e82-272">During marshaling, the variant is converted to a <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13e82-273">Si **Object** est ensuite repassé à COM, il est remarshalé vers un variant de type **VT_UNKNOWN**.</span><span class="sxs-lookup"><span data-stu-id="13e82-273">If the **Object** is then passed back to COM, it is marshaled back to a variant of type **VT_UNKNOWN**.</span></span> <span data-ttu-id="13e82-274">Rien ne garantit que le variant produit quand un objet est marshalé à partir de code managé vers COM sera du même type que le variant utilisé à l’origine pour produire l’objet.</span><span class="sxs-lookup"><span data-stu-id="13e82-274">There is no guarantee that the variant produced when an object is marshaled from managed code to COM will be the same type as the variant initially used to produce the object.</span></span>

## <a name="marshaling-byref-variants"></a><span data-ttu-id="13e82-275">Marshaling des variants ByRef</span><span class="sxs-lookup"><span data-stu-id="13e82-275">Marshaling ByRef Variants</span></span>

<span data-ttu-id="13e82-276">Bien que les variants puissent eux-mêmes être passés par valeur ou par référence, l’indicateur **VT_BYREF** peut être également utilisé avec n’importe quel type de variant pour indiquer que le contenu du variant est passé par référence plutôt que par valeur.</span><span class="sxs-lookup"><span data-stu-id="13e82-276">Although variants themselves can be passed by value or by reference, the **VT_BYREF** flag can also be used with any variant type to indicate that the contents of the variant are being passed by reference instead of by value.</span></span> <span data-ttu-id="13e82-277">La différence entre le marshaling de variants par référence et le marshaling d’un variant dont l’indicateur **VT_BYREF** est défini peut prêter à confusion.</span><span class="sxs-lookup"><span data-stu-id="13e82-277">The difference between marshaling variants by reference and marshaling a variant with the **VT_BYREF** flag set can be confusing.</span></span> <span data-ttu-id="13e82-278">L’illustration suivante clarifie ces différences :</span><span class="sxs-lookup"><span data-stu-id="13e82-278">The following illustration clarifies the differences:</span></span>

<span data-ttu-id="13e82-279">![Diagramme illustrant une variante transmise à la pile.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span><span class="sxs-lookup"><span data-stu-id="13e82-279">![Diagram that shows variant passed on the stack.](./media/default-marshaling-for-objects/interop-variant-passed-value-reference.gif)</span></span>
<span data-ttu-id="13e82-280">Variants passés par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="13e82-280">Variants passed by value and by reference</span></span>

<span data-ttu-id="13e82-281">**Comportement par défaut de marshaling d’objets et de variants par valeur**</span><span class="sxs-lookup"><span data-stu-id="13e82-281">**Default behavior for marshaling objects and variants by value**</span></span>

- <span data-ttu-id="13e82-282">Lors du passage d’objets à partir de code managé vers COM, le contenu de l’objet est copié dans un nouveau variant créé par le marshaleur à l’aide des règles définies dans [Marshaling d’un objet vers un variant](#marshaling-object-to-variant).</span><span class="sxs-lookup"><span data-stu-id="13e82-282">When passing objects from managed code to COM, the contents of the object are copied into a new variant created by the marshaler, using the rules defined in [Marshaling Object to Variant](#marshaling-object-to-variant).</span></span> <span data-ttu-id="13e82-283">Les changements apportés au variant côté non managé ne sont pas retournés vers l’objet d’origine au retour de l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-283">Changes made to the variant on the unmanaged side are not propagated back to the original object on return from the call.</span></span>

- <span data-ttu-id="13e82-284">Lors du passage de variants à partir de COM vers du code managé, le contenu du variant est copié dans un objet nouvellement créé à l’aide des règles définies dans [Marshaling d’un variant vers un objet](#marshaling-variant-to-object).</span><span class="sxs-lookup"><span data-stu-id="13e82-284">When passing variants from COM to managed code, the contents of the variant are copied to a newly created object, using the rules defined in [Marshaling Variant to Object](#marshaling-variant-to-object).</span></span> <span data-ttu-id="13e82-285">Les changements apportés à l’objet côté managé ne sont pas retournés vers le variant d’origine au retour de l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-285">Changes made to the object on the managed side are not propagated back to the original variant on return from the call.</span></span>

<span data-ttu-id="13e82-286">**Comportement par défaut de marshaling d’objets et de variants par référence**</span><span class="sxs-lookup"><span data-stu-id="13e82-286">**Default behavior for marshaling objects and variants by reference**</span></span>

<span data-ttu-id="13e82-287">Pour retourner des changements à l’appelant, les paramètres doivent être passés par référence.</span><span class="sxs-lookup"><span data-stu-id="13e82-287">To propagate changes back to the caller, the parameters must be passed by reference.</span></span> <span data-ttu-id="13e82-288">Par exemple, vous pouvez utiliser le mot clé **ref** en C# (ou **ByRef** en code managé Visual Basic) pour passer des paramètres par référence.</span><span class="sxs-lookup"><span data-stu-id="13e82-288">For example, you can use the **ref** keyword in C# (or **ByRef** in Visual Basic managed code) to pass parameters by reference.</span></span> <span data-ttu-id="13e82-289">Dans COM, les paramètres de référence sont passés à l’aide d’un pointeur tel que **variant \***.</span><span class="sxs-lookup"><span data-stu-id="13e82-289">In COM, reference parameters are passed using a pointer such as a **variant \***.</span></span>

- <span data-ttu-id="13e82-290">Lors du passage d’un objet à COM par référence, le marshaleur crée un variant et copie le contenu de la référence d’objet dans le variant avant que l’appel ne soit effectué.</span><span class="sxs-lookup"><span data-stu-id="13e82-290">When passing an object to COM by reference, the marshaler creates a new variant and copies the contents of the object reference into the variant before the call is made.</span></span> <span data-ttu-id="13e82-291">Le variant est passé à la fonction non managée où l’utilisateur est libre de changer le contenu du variant.</span><span class="sxs-lookup"><span data-stu-id="13e82-291">The variant is passed to the unmanaged function where the user is free to change the contents of the variant.</span></span> <span data-ttu-id="13e82-292">Au retour de l’appel, tout changement apporté au variant côté non managé est retourné vers l’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="13e82-292">On return from the call, any changes made to the variant on the unmanaged side are propagated back to the original object.</span></span> <span data-ttu-id="13e82-293">Si le type de variant est différent du type du variant passé à l’appel, les changements sont retournés à un objet d’un type différent.</span><span class="sxs-lookup"><span data-stu-id="13e82-293">If the type of the variant differs from the type of the variant passed to the call, then the changes are propagated back to an object of a different type.</span></span> <span data-ttu-id="13e82-294">Cela signifie que le type de l’objet passé dans l’appel peut être différent du type de l’objet retourné à partir de l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-294">That is, the type of the object passed into the call can differ from the type of the object returned from the call.</span></span>

- <span data-ttu-id="13e82-295">Lors du passage d’un variant au code managé par référence, le marshaleur crée un objet et copie le contenu du variant dans l’objet avant que l’appel ne soit effectué.</span><span class="sxs-lookup"><span data-stu-id="13e82-295">When passing a variant to managed code by reference, the marshaler creates a new object and copies the contents of the variant into the object before making the call.</span></span> <span data-ttu-id="13e82-296">Une référence à l’objet est passée à la fonction managée, où l’utilisateur est libre de changer l’objet.</span><span class="sxs-lookup"><span data-stu-id="13e82-296">A reference to the object is passed to the managed function, where the user is free to change the object.</span></span> <span data-ttu-id="13e82-297">Au retour de l’appel, tout changement apporté à l’objet référencé est retourné vers le variant d’origine.</span><span class="sxs-lookup"><span data-stu-id="13e82-297">On return from the call, any changes made to the referenced object are propagated back to the original variant.</span></span> <span data-ttu-id="13e82-298">Si le type de l’objet est différent du type de l’objet passé dans l’appel, le type du variant d’origine est changé et la valeur est retournée dans le variant.</span><span class="sxs-lookup"><span data-stu-id="13e82-298">If the type of the object differs from the type of the object passed in to the call, the type of the original variant is changed and the value is propagated back into the variant.</span></span> <span data-ttu-id="13e82-299">Là encore, le type du variant passé dans l’appel peut être différent du type du variant retourné à partir de l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-299">Again, the type of the variant passed into the call can differ from the type of the variant returned from the call.</span></span>

 <span data-ttu-id="13e82-300">**Comportement par défaut de marshaling d’un variant dont l’indicateur VT_BYREF est défini**</span><span class="sxs-lookup"><span data-stu-id="13e82-300">**Default behavior for marshaling a variant with the VT_BYREF flag set**</span></span>

- <span data-ttu-id="13e82-301">Un variant passé à du code managé par valeur peut avoir l’indicateur **VT_BYREF** défini pour indiquer que le variant contient une référence plutôt qu’une valeur.</span><span class="sxs-lookup"><span data-stu-id="13e82-301">A variant being passed to managed code by value can have the **VT_BYREF** flag set to indicate that the variant contains a reference instead of a value.</span></span> <span data-ttu-id="13e82-302">Dans ce cas, le variant est toujours marshalé vers un objet, car le variant est passé par valeur.</span><span class="sxs-lookup"><span data-stu-id="13e82-302">In this case, the variant is still marshaled to an object because the variant is being passed by value.</span></span> <span data-ttu-id="13e82-303">Le marshaleur déréférence automatiquement le contenu du variant et le copie dans un objet nouvellement créé avant d’effectuer l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-303">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="13e82-304">L’objet est ensuite passé à la fonction managée ; cependant, au retour de l’appel, l’objet n’est pas retourné dans le variant d’origine.</span><span class="sxs-lookup"><span data-stu-id="13e82-304">The object is then passed into the managed function; however, on return from the call, the object is not propagated back into the original variant.</span></span> <span data-ttu-id="13e82-305">Les changements apportés à l’objet managé sont perdus.</span><span class="sxs-lookup"><span data-stu-id="13e82-305">Changes made to the managed object are lost.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="13e82-306">Il est impossible de changer la valeur d’un variant passé par valeur, même si l’indicateur **VT_BYREF** de ce variant est défini.</span><span class="sxs-lookup"><span data-stu-id="13e82-306">There is no way to change the value of a variant passed by value, even if the variant has the **VT_BYREF** flag set.</span></span>

- <span data-ttu-id="13e82-307">Un variant passé à du code managé par référence peut aussi avoir l’indicateur **VT_BYREF** défini pour indiquer que le variant contient une autre référence.</span><span class="sxs-lookup"><span data-stu-id="13e82-307">A variant being passed to managed code by reference can also have the **VT_BYREF** flag set to indicate that the variant contains another reference.</span></span> <span data-ttu-id="13e82-308">Si c’est le cas, le variant est marshalé vers un objet **ref** parce qu’il est passé par référence.</span><span class="sxs-lookup"><span data-stu-id="13e82-308">If it does, the variant is marshaled to a **ref** object because the variant is being passed by reference.</span></span> <span data-ttu-id="13e82-309">Le marshaleur déréférence automatiquement le contenu du variant et le copie dans un objet nouvellement créé avant d’effectuer l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-309">The marshaler automatically dereferences the contents of the variant and copies it into a newly created object before making the call.</span></span> <span data-ttu-id="13e82-310">Au retour de l’appel, la valeur de l’objet est retournée vers la référence située dans le variant d’origine uniquement si l’objet est du même type que l’objet passé.</span><span class="sxs-lookup"><span data-stu-id="13e82-310">On return from the call, the value of the object is propagated back to the reference within the original variant only if the object is the same type as the object passed in.</span></span> <span data-ttu-id="13e82-311">Autrement dit, la propagation ne change pas le type d’un variant avec l’indicateur **VT_BYREF** défini.</span><span class="sxs-lookup"><span data-stu-id="13e82-311">That is, propagation does not change the type of a variant with the **VT_BYREF** flag set.</span></span> <span data-ttu-id="13e82-312">Si le type de l’objet est modifié durant l’appel, une exception <xref:System.InvalidCastException> se produit au retour de l’appel.</span><span class="sxs-lookup"><span data-stu-id="13e82-312">If the type of the object is changed during the call, an <xref:System.InvalidCastException> occurs on return from the call.</span></span>

<span data-ttu-id="13e82-313">Le tableau suivant résume les règles de propagation pour les variants et les objets.</span><span class="sxs-lookup"><span data-stu-id="13e82-313">The following table summarizes the propagation rules for variants and objects.</span></span>

|<span data-ttu-id="13e82-314">À partir</span><span class="sxs-lookup"><span data-stu-id="13e82-314">From</span></span>|<span data-ttu-id="13e82-315">À</span><span class="sxs-lookup"><span data-stu-id="13e82-315">To</span></span>|<span data-ttu-id="13e82-316">Changements retournés</span><span class="sxs-lookup"><span data-stu-id="13e82-316">Changes propagated back</span></span>|
|----------|--------|-----------------------------|
|<span data-ttu-id="13e82-317">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="13e82-317">**Variant**  *v*</span></span>|<span data-ttu-id="13e82-318">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="13e82-318">**Object**  *o*</span></span>|<span data-ttu-id="13e82-319">Jamais</span><span class="sxs-lookup"><span data-stu-id="13e82-319">Never</span></span>|
|<span data-ttu-id="13e82-320">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="13e82-320">**Object**  *o*</span></span>|<span data-ttu-id="13e82-321">**Variant**  *v*</span><span class="sxs-lookup"><span data-stu-id="13e82-321">**Variant**  *v*</span></span>|<span data-ttu-id="13e82-322">Jamais</span><span class="sxs-lookup"><span data-stu-id="13e82-322">Never</span></span>|
|<span data-ttu-id="13e82-323">**Variante** ***\**** *PV*     </span><span class="sxs-lookup"><span data-stu-id="13e82-323">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="13e82-324">**Ref Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="13e82-324">**Ref Object**  *o*</span></span>|<span data-ttu-id="13e82-325">Toujours</span><span class="sxs-lookup"><span data-stu-id="13e82-325">Always</span></span>|
|<span data-ttu-id="13e82-326">**Objet Ref**  *o*</span><span class="sxs-lookup"><span data-stu-id="13e82-326">**Ref object**  *o*</span></span>|<span data-ttu-id="13e82-327">**Variante** ***\**** *PV*     </span><span class="sxs-lookup"><span data-stu-id="13e82-327">**Variant**   ***\****  *pv*</span></span>|<span data-ttu-id="13e82-328">Toujours</span><span class="sxs-lookup"><span data-stu-id="13e82-328">Always</span></span>|
|<span data-ttu-id="13e82-329">**Variante**  *v* **(VT_BYREF** *&#124;* **VT_ \* )**</span><span class="sxs-lookup"><span data-stu-id="13e82-329">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_\*)**</span></span>|<span data-ttu-id="13e82-330">**Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="13e82-330">**Object**  *o*</span></span>|<span data-ttu-id="13e82-331">Jamais</span><span class="sxs-lookup"><span data-stu-id="13e82-331">Never</span></span>|
|<span data-ttu-id="13e82-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span><span class="sxs-lookup"><span data-stu-id="13e82-332">**Variant**  *v* **(VT_BYREF** *&#124;* **VT_)**</span></span>|<span data-ttu-id="13e82-333">**Ref Object**  *o*</span><span class="sxs-lookup"><span data-stu-id="13e82-333">**Ref Object**  *o*</span></span>|<span data-ttu-id="13e82-334">Uniquement si le type n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="13e82-334">Only if the type has not changed.</span></span>|

## <a name="see-also"></a><span data-ttu-id="13e82-335">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13e82-335">See also</span></span>

- [<span data-ttu-id="13e82-336">comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="13e82-336">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="13e82-337">types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="13e82-337">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="13e82-338">[Attributs directionnels](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="13e82-338">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="13e82-339">copie et épinglage</span><span class="sxs-lookup"><span data-stu-id="13e82-339">Copying and Pinning</span></span>](copying-and-pinning.md)
