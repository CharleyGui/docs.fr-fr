---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 00485ff80a0064e700d99203de3aa581d3761f30
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255726"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="4388c-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4388c-102">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="4388c-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4388c-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4388c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4388c-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4388c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4388c-105">Methods</span></span>  

 <span data-ttu-id="4388c-106">La classe AsymmetricSecurityBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="4388c-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4388c-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4388c-107">Properties</span></span>  

 <span data-ttu-id="4388c-108">La classe AsymmetricSecurityBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4388c-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="4388c-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="4388c-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="4388c-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="4388c-110">Data type: string</span></span>  
  
 <span data-ttu-id="4388c-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="4388c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4388c-112">Ordre de chiffrement et de signature des messages de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4388c-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="4388c-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="4388c-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="4388c-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="4388c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4388c-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="4388c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4388c-116">Si la liaison requiert la confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="4388c-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4388c-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4388c-117">Requirements</span></span>  
  
|<span data-ttu-id="4388c-118">MOF</span><span class="sxs-lookup"><span data-stu-id="4388c-118">MOF</span></span>|<span data-ttu-id="4388c-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4388c-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4388c-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="4388c-120">Namespace</span></span>|<span data-ttu-id="4388c-121">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4388c-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4388c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4388c-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
