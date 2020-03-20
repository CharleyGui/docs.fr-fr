---
title: 'Comment : créer une revendication personnalisée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: e78f577e0fd3473575fab998e55616936212ebb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185618"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="143f4-102">Comment : créer une revendication personnalisée</span><span class="sxs-lookup"><span data-stu-id="143f4-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="143f4-103">L’infrastructure Identity Model de windows Communication Foundation (WCF) fournit un ensemble de types <xref:System.IdentityModel.Claims.Claim> et de droits intégrés de réclamation avec les fonctions d’aide pour créer des instances avec ces types et droits.</span><span class="sxs-lookup"><span data-stu-id="143f4-103">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="143f4-104">Ces réclamations intégrées sont conçues pour modéliser les informations trouvées dans les types d’identification des clients que WCF prend en charge par défaut.</span><span class="sxs-lookup"><span data-stu-id="143f4-104">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="143f4-105">Dans la plupart des cas, les revendications intégrées sont suffisantes ; toutefois, certaines applications peuvent requérir des revendications personnalisées.</span><span class="sxs-lookup"><span data-stu-id="143f4-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="143f4-106">Une revendication comporte trois volets : le type de revendication, la ressource à laquelle la revendication s'applique et le droit revendiqué sur cette ressource.</span><span class="sxs-lookup"><span data-stu-id="143f4-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="143f4-107">Cette rubrique décrit comment créer une revendication personnalisée.</span><span class="sxs-lookup"><span data-stu-id="143f4-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="143f4-108">Pour créer une revendication personnalisée basée sur un type de données primitif</span><span class="sxs-lookup"><span data-stu-id="143f4-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="143f4-109">Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="143f4-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="143f4-110">Choisissez une valeur unique pour le type de revendication.</span><span class="sxs-lookup"><span data-stu-id="143f4-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="143f4-111">Le type de revendication est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="143f4-112">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="143f4-113">Pour une liste de types de réclamations <xref:System.IdentityModel.Claims.ClaimTypes> qui sont définis par WCF, voir la classe.</span><span class="sxs-lookup"><span data-stu-id="143f4-113">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="143f4-114">Choisissez le type de données primitif et la valeur de la ressource.</span><span class="sxs-lookup"><span data-stu-id="143f4-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="143f4-115">Une ressource est un objet.</span><span class="sxs-lookup"><span data-stu-id="143f4-115">A resource is an object.</span></span> <span data-ttu-id="143f4-116">Le type CLR de la ressource peut être une primitive, telle que <xref:System.String> ou <xref:System.Int32>, ou tout type sérialisable.</span><span class="sxs-lookup"><span data-stu-id="143f4-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="143f4-117">Le type CLR de la ressource doit être sérialisable, parce que les revendications sont sérialisées à divers moments par WCF.</span><span class="sxs-lookup"><span data-stu-id="143f4-117">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="143f4-118">Les types primitifs sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="143f4-118">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="143f4-119">Choisissez un droit qui est défini par WCF ou une valeur unique pour un droit personnalisé.</span><span class="sxs-lookup"><span data-stu-id="143f4-119">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="143f4-120">Un droit est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-120">A right is a unique string identifier.</span></span> <span data-ttu-id="143f4-121">Les droits définis par WCF <xref:System.IdentityModel.Claims.Rights> sont définis dans la classe.</span><span class="sxs-lookup"><span data-stu-id="143f4-121">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="143f4-122">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="143f4-123">L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/simplecustomclaim`, pour une ressource nommée `Driver's License`, et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="143f4-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="143f4-124">Pour créer une revendication personnalisée basée sur un type de données non primitif</span><span class="sxs-lookup"><span data-stu-id="143f4-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="143f4-125">Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="143f4-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="143f4-126">Choisissez une valeur unique pour le type de revendication.</span><span class="sxs-lookup"><span data-stu-id="143f4-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="143f4-127">Le type de revendication est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="143f4-128">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="143f4-129">Pour une liste de types de réclamations <xref:System.IdentityModel.Claims.ClaimTypes> qui sont définis par WCF, voir la classe.</span><span class="sxs-lookup"><span data-stu-id="143f4-129">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="143f4-130">Choisissez ou définissez un type non primitif sérialisable pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="143f4-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="143f4-131">Une ressource est un objet.</span><span class="sxs-lookup"><span data-stu-id="143f4-131">A resource is an object.</span></span> <span data-ttu-id="143f4-132">Le type CLR de la ressource doit être sérialisable, parce que les revendications sont sérialisées à divers moments par WCF.</span><span class="sxs-lookup"><span data-stu-id="143f4-132">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="143f4-133">Les types primitifs sont déjà sérialisables.</span><span class="sxs-lookup"><span data-stu-id="143f4-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="143f4-134">Lorsqu'un nouveau type est défini, appliquez <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="143f4-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="143f4-135">Appliquez également l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à tous les membres du nouveau type qui doivent être sérialisés dans le cadre de la revendication.</span><span class="sxs-lookup"><span data-stu-id="143f4-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="143f4-136">L'exemple de code suivant définit un type de ressource personnalisé nommé `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="143f4-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="143f4-137">Choisissez un droit qui est défini par WCF ou une valeur unique pour un droit personnalisé.</span><span class="sxs-lookup"><span data-stu-id="143f4-137">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="143f4-138">Un droit est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-138">A right is a unique string identifier.</span></span> <span data-ttu-id="143f4-139">Les droits définis par WCF <xref:System.IdentityModel.Claims.Rights> sont définis dans la classe.</span><span class="sxs-lookup"><span data-stu-id="143f4-139">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="143f4-140">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.</span><span class="sxs-lookup"><span data-stu-id="143f4-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="143f4-141">L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/complexcustomclaim`, un type de ressource personnalisé `MyResourceType` et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="143f4-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="143f4-142"> Exemple</span><span class="sxs-lookup"><span data-stu-id="143f4-142">Example</span></span>  
 <span data-ttu-id="143f4-143">L'exemple de code suivant montre comment créer une revendication personnalisée avec un type de ressource primitif et un type de ressource non primitif.</span><span class="sxs-lookup"><span data-stu-id="143f4-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="143f4-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="143f4-144">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="143f4-145">Gestion des revendications et autorisation avec le modèle d'identité</span><span class="sxs-lookup"><span data-stu-id="143f4-145">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
