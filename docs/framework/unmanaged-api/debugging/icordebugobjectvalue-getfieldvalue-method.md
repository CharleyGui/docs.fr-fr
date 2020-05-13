---
title: ICorDebugObjectValue::GetFieldValue, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207595"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a><span data-ttu-id="c66ac-102">ICorDebugObjectValue::GetFieldValue, méthode</span><span class="sxs-lookup"><span data-stu-id="c66ac-102">ICorDebugObjectValue::GetFieldValue Method</span></span>
<span data-ttu-id="c66ac-103">Obtient la valeur du champ spécifié de la classe spécifiée pour cette valeur d’objet.</span><span class="sxs-lookup"><span data-stu-id="c66ac-103">Gets the value of the specified field of the specified class for this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c66ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c66ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c66ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c66ac-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="c66ac-106">dans Pointeur vers un objet « ICorDebugClass » qui représente la classe pour laquelle obtenir la valeur de champ.</span><span class="sxs-lookup"><span data-stu-id="c66ac-106">[in] A pointer to an "ICorDebugClass" object that represents the class for which to get the field value.</span></span>  
  
 `fieldDef`  
 <span data-ttu-id="c66ac-107">dans `mdFieldDef`Jeton qui fait référence aux métadonnées décrivant le champ.</span><span class="sxs-lookup"><span data-stu-id="c66ac-107">[in] An `mdFieldDef` token that references the metadata describing the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="c66ac-108">à Pointeur vers un objet « ICorDebugValue » qui représente la valeur du champ spécifié.</span><span class="sxs-lookup"><span data-stu-id="c66ac-108">[out] A pointer to an "ICorDebugValue" object that represents the value of the specified field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c66ac-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c66ac-109">Remarks</span></span>  
 <span data-ttu-id="c66ac-110">La classe, spécifiée dans le `pClass` paramètre, doit se trouver dans la hiérarchie de la classe de la valeur de l’objet, et le champ doit être un champ de cette classe.</span><span class="sxs-lookup"><span data-stu-id="c66ac-110">The class, specified in the `pClass` parameter, must be in the hierarchy of the object value's class, and the field must be a field of that class.</span></span>  
  
 <span data-ttu-id="c66ac-111">La `GetFieldValue` méthode continuera d’être exécutée pour les objets génériques et les classes génériques.</span><span class="sxs-lookup"><span data-stu-id="c66ac-111">The `GetFieldValue` method will still succeed for generic objects and generic classes.</span></span> <span data-ttu-id="c66ac-112">Par exemple, si MyDictionary \< v> hérite de \< la chaîne de dictionnaire, v> et que la valeur de l’objet est de type MyDictionary \< Int32>, passant l' `ICorDebugClass` objet pour le dictionnaire \< K, v> obtiendra avec succès un champ de chaîne de dictionnaire \< , Int32>.</span><span class="sxs-lookup"><span data-stu-id="c66ac-112">For example, if MyDictionary\<V> inherits from Dictionary\<string,V>, and the object value is of type MyDictionary\<int32>, passing the `ICorDebugClass` object for Dictionary\<K,V> will successfully get a field of Dictionary\<string,int32>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c66ac-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c66ac-113">Requirements</span></span>  
 <span data-ttu-id="c66ac-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c66ac-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c66ac-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c66ac-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c66ac-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c66ac-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c66ac-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c66ac-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66ac-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c66ac-118">See also</span></span>
