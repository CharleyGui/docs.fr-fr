---
title: CorNativeType, énumération
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: dd97c479f12e7bdb015b39a802b398ca2b0bcd3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007635"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="5d1a4-102">CorNativeType, énumération</span><span class="sxs-lookup"><span data-stu-id="5d1a4-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="5d1a4-103">Contient des valeurs qui décrivent les types non managés natifs.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d1a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d1a4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="5d1a4-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5d1a4-105">Members</span></span>  
  
|<span data-ttu-id="5d1a4-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5d1a4-106">Member</span></span>|<span data-ttu-id="5d1a4-107">Description</span><span class="sxs-lookup"><span data-stu-id="5d1a4-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="5d1a4-108">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="5d1a4-109">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="5d1a4-110">Valeur booléenne sur 4 octets, où TRUE est différent de zéro et FALSe est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="5d1a4-111">Valeur entière 8 bits signée.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="5d1a4-112">Valeur entière 8 bits non signée.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="5d1a4-113">Valeur entière 16 bits signée.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="5d1a4-114">Valeur entière 16 bits non signée.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="5d1a4-115">Valeur d’entier 32 bits signé.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="5d1a4-116">Valeur d'entier 32 bits non signé.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="5d1a4-117">Valeur entière 64 bits signée.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="5d1a4-118">Valeur entière 64 bits non signée.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="5d1a4-119">Valeur numérique à virgule flottante sur 4 octets.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="5d1a4-120">Valeur numérique à virgule flottante sur 8 octets.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="5d1a4-121">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="5d1a4-122">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="5d1a4-123">Type COM numérique qui correspond au <xref:System.Decimal> type managé.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="5d1a4-124">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="5d1a4-125">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="5d1a4-126">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="5d1a4-127">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="5d1a4-128">Valeur de chaîne LPSTR.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="5d1a4-129">Valeur de chaîne LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="5d1a4-130">Valeur de chaîne LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="5d1a4-131">Valeur de chaîne fixe définie par le système.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="5d1a4-132">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="5d1a4-133">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="5d1a4-134">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="5d1a4-135">Valeur de structure native.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="5d1a4-136">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="5d1a4-137">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="5d1a4-138">Valeur de tableau de longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="5d1a4-139">Valeur d’entier 16 bits signé natif.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="5d1a4-140">Valeur de l’entier non signé 16 bits natif.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="5d1a4-141">Obsolète.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="5d1a4-142">Utilisez NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="5d1a4-143">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="5d1a4-144">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="5d1a4-145">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="5d1a4-146">Sélectionnez BSTR ou ANSIBSTR en fonction de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="5d1a4-147">Valeur booléenne sur 2 octets, où TRUE est-1 et FALSe est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="5d1a4-148">Pointeur de fonction.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="5d1a4-149">Référence à n’importe quel type natif.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="5d1a4-150">Référence à un tableau avec des membres d’un type non spécifié.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="5d1a4-151">Pointeur d’entier 32 bits vers une structure.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="5d1a4-152">Type natif de marshaleur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="5d1a4-153">Il doit être suivi d’une chaîne au format suivant : « nom de type natif/nom de type de marshaleur 0Custom/0Optional cookie/0 » ou « {native type GUID}/0Custom nom de type de marshaleur/0Optional cookie/0 »</span><span class="sxs-lookup"><span data-stu-id="5d1a4-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="5d1a4-154">COM Interop.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="5d1a4-155">Avec ELEMENT_TYPE_I4 ce type est mappé à VT_HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="5d1a4-156">Type natif `IInspectable` .</span><span class="sxs-lookup"><span data-stu-id="5d1a4-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="5d1a4-157">Un natif `HString` .</span><span class="sxs-lookup"><span data-stu-id="5d1a4-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="5d1a4-158">Valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="5d1a4-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d1a4-159">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5d1a4-159">Requirements</span></span>  
 <span data-ttu-id="5d1a4-160">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d1a4-160">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d1a4-161">**En-tête :** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="5d1a4-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5d1a4-162">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d1a4-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d1a4-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d1a4-163">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="5d1a4-164">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="5d1a4-164">Metadata Enumerations</span></span>](metadata-enumerations.md)
