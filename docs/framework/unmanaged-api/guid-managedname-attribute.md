---
title: GUID_ManagedName, attribut
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
ms.openlocfilehash: 0127b6894f1095521f1b24fc8c0424dc7db824b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721047"
---
# <a name="guid_managedname-attribute"></a><span data-ttu-id="a9eb5-102">GUID_ManagedName, attribut</span><span class="sxs-lookup"><span data-stu-id="a9eb5-102">GUID_ManagedName Attribute</span></span>

<span data-ttu-id="a9eb5-103">Définit un attribut d’interface personnalisé qui spécifie le nom de l’espace de noms managé pour une bibliothèque COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="a9eb5-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9eb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9eb5-104">Syntax</span></span>  
  
```idl
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9eb5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9eb5-105">Parameters</span></span>  

 `value`  
 <span data-ttu-id="a9eb5-106">Nom de l’espace de noms managé pour la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a9eb5-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="a9eb5-107">Définition</span><span class="sxs-lookup"><span data-stu-id="a9eb5-107">Definition</span></span>  

 <span data-ttu-id="a9eb5-108">`GUID_ManagedName` est défini dans Cor. h comme suit :</span><span class="sxs-lookup"><span data-stu-id="a9eb5-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```cpp
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a9eb5-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="a9eb5-109">Remarks</span></span>  

 <span data-ttu-id="a9eb5-110">Un attribut d’interface personnalisé définit les métadonnées d’un objet dans la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="a9eb5-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="a9eb5-111">Utilisez <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> ou <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> pour récupérer le nom managé de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="a9eb5-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="a9eb5-112">Pour plus d’informations, consultez [attributs d’interface](/cpp/windows/attributes/interface-attributes) dans la documentation de référence Visual C++.</span><span class="sxs-lookup"><span data-stu-id="a9eb5-112">For more information, see [Interface Attributes](/cpp/windows/attributes/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9eb5-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a9eb5-113">Example</span></span>  

 <span data-ttu-id="a9eb5-114">L’exemple suivant montre une définition de bibliothèque à l’aide de l' `GUID_ManagedName` attribut.</span><span class="sxs-lookup"><span data-stu-id="a9eb5-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```idl
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="a9eb5-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a9eb5-115">Requirements</span></span>  

 <span data-ttu-id="a9eb5-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a9eb5-116">**Header:** Cor.h</span></span>
