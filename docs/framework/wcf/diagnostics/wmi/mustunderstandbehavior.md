---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 9cac7192d5c34de55fe0bd6a4921a41387e985f8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250435"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="0b38a-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="0b38a-102">MustUnderstandBehavior</span></span>

<span data-ttu-id="0b38a-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="0b38a-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b38a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b38a-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0b38a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0b38a-105">Methods</span></span>  

 <span data-ttu-id="0b38a-106">La classe MustUnderstandBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="0b38a-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0b38a-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="0b38a-107">Properties</span></span>  

 <span data-ttu-id="0b38a-108">La classe MustUnderstandBehavior a la propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="0b38a-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="0b38a-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="0b38a-109">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="0b38a-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="0b38a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="0b38a-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="0b38a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0b38a-112">Lorsque cette propriété a la valeur `true`, tous les en-têtes SOAP avec l'attribut `MustUnderstand` qui ne sont pas gérés font en sorte que le comportement lève une exception.</span><span class="sxs-lookup"><span data-stu-id="0b38a-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b38a-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0b38a-113">Requirements</span></span>  
  
|<span data-ttu-id="0b38a-114">MOF</span><span class="sxs-lookup"><span data-stu-id="0b38a-114">MOF</span></span>|<span data-ttu-id="0b38a-115">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0b38a-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0b38a-116">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="0b38a-116">Namespace</span></span>|<span data-ttu-id="0b38a-117">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0b38a-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0b38a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b38a-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>
