---
title: 'Comment : créer une revendication personnalisée'
description: Découvrez comment créer une revendication personnalisée dans WCF. WCF prend en charge diverses revendications intégrées et certaines applications peuvent nécessiter des revendications personnalisées.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
ms.openlocfilehash: 89f2b1359b48b71720db6ff38f27883745cfe612
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247544"
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="253aa-104">Comment : créer une revendication personnalisée</span><span class="sxs-lookup"><span data-stu-id="253aa-104">How to: Create a Custom Claim</span></span>
<span data-ttu-id="253aa-105">L’infrastructure de modèle d’identité dans Windows Communication Foundation (WCF) fournit un ensemble de types de revendication intégrés et des droits avec les fonctions d’assistance pour créer des <xref:System.IdentityModel.Claims.Claim> instances avec ces types et droits.</span><span class="sxs-lookup"><span data-stu-id="253aa-105">The Identity Model infrastructure in Windows Communication Foundation (WCF) provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="253aa-106">Ces revendications intégrées sont conçues pour modéliser les informations qui se trouvent dans les types d’informations d’identification du client prises en charge par WCF par défaut.</span><span class="sxs-lookup"><span data-stu-id="253aa-106">These built-in claims are designed to model information found in client credential types that WCF supports by default.</span></span> <span data-ttu-id="253aa-107">Dans la plupart des cas, les revendications intégrées sont suffisantes ; toutefois, certaines applications peuvent requérir des revendications personnalisées.</span><span class="sxs-lookup"><span data-stu-id="253aa-107">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="253aa-108">Une revendication comporte trois volets : le type de revendication, la ressource à laquelle la revendication s'applique et le droit revendiqué sur cette ressource.</span><span class="sxs-lookup"><span data-stu-id="253aa-108">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="253aa-109">Cette rubrique décrit comment créer une revendication personnalisée.</span><span class="sxs-lookup"><span data-stu-id="253aa-109">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="253aa-110">Pour créer une revendication personnalisée basée sur un type de données primitif</span><span class="sxs-lookup"><span data-stu-id="253aa-110">To create a custom claim that is based on a primitive data type</span></span>  
  
1. <span data-ttu-id="253aa-111">Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="253aa-111">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="253aa-112">Choisissez une valeur unique pour le type de revendication.</span><span class="sxs-lookup"><span data-stu-id="253aa-112">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="253aa-113">Le type de revendication est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-113">The claim type is a unique string identifier.</span></span> <span data-ttu-id="253aa-114">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-114">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="253aa-115">Pour obtenir la liste des types de revendications définis par WCF, consultez la <xref:System.IdentityModel.Claims.ClaimTypes> classe.</span><span class="sxs-lookup"><span data-stu-id="253aa-115">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="253aa-116">Choisissez le type de données primitif et la valeur de la ressource.</span><span class="sxs-lookup"><span data-stu-id="253aa-116">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="253aa-117">Une ressource est un objet.</span><span class="sxs-lookup"><span data-stu-id="253aa-117">A resource is an object.</span></span> <span data-ttu-id="253aa-118">Le type CLR de la ressource peut être une primitive, telle que <xref:System.String> ou <xref:System.Int32>, ou tout type sérialisable.</span><span class="sxs-lookup"><span data-stu-id="253aa-118">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="253aa-119">Le type CLR de la ressource doit être sérialisable, car les revendications sont sérialisées à différents points par WCF.</span><span class="sxs-lookup"><span data-stu-id="253aa-119">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="253aa-120">Les types primitifs sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="253aa-120">Primitive types are serializable.</span></span>  
  
    3. <span data-ttu-id="253aa-121">Choisissez un droit défini par WCF ou une valeur unique pour un droit personnalisé.</span><span class="sxs-lookup"><span data-stu-id="253aa-121">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="253aa-122">Un droit est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-122">A right is a unique string identifier.</span></span> <span data-ttu-id="253aa-123">Les droits définis par WCF sont définis dans la <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="253aa-123">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="253aa-124">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-124">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="253aa-125">L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/simplecustomclaim`, pour une ressource nommée `Driver's License`, et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="253aa-125">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="253aa-126">Pour créer une revendication personnalisée basée sur un type de données non primitif</span><span class="sxs-lookup"><span data-stu-id="253aa-126">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1. <span data-ttu-id="253aa-127">Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="253aa-127">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1. <span data-ttu-id="253aa-128">Choisissez une valeur unique pour le type de revendication.</span><span class="sxs-lookup"><span data-stu-id="253aa-128">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="253aa-129">Le type de revendication est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-129">The claim type is a unique string identifier.</span></span> <span data-ttu-id="253aa-130">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-130">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="253aa-131">Pour obtenir la liste des types de revendications définis par WCF, consultez la <xref:System.IdentityModel.Claims.ClaimTypes> classe.</span><span class="sxs-lookup"><span data-stu-id="253aa-131">For a list of claim types that are defined by WCF, see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2. <span data-ttu-id="253aa-132">Choisissez ou définissez un type non primitif sérialisable pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="253aa-132">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="253aa-133">Une ressource est un objet.</span><span class="sxs-lookup"><span data-stu-id="253aa-133">A resource is an object.</span></span> <span data-ttu-id="253aa-134">Le type CLR de la ressource doit être sérialisable, car les revendications sont sérialisées à différents points par WCF.</span><span class="sxs-lookup"><span data-stu-id="253aa-134">The CLR type of the resource must be serializable, because claims are serialized at various points by WCF.</span></span> <span data-ttu-id="253aa-135">Les types primitifs sont déjà sérialisables.</span><span class="sxs-lookup"><span data-stu-id="253aa-135">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="253aa-136">Lorsqu'un nouveau type est défini, appliquez <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="253aa-136">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="253aa-137">Appliquez également l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à tous les membres du nouveau type qui doivent être sérialisés dans le cadre de la revendication.</span><span class="sxs-lookup"><span data-stu-id="253aa-137">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="253aa-138">L'exemple de code suivant définit un type de ressource personnalisé nommé `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="253aa-138">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. <span data-ttu-id="253aa-139">Choisissez un droit défini par WCF ou une valeur unique pour un droit personnalisé.</span><span class="sxs-lookup"><span data-stu-id="253aa-139">Choose a right that is defined by WCF or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="253aa-140">Un droit est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-140">A right is a unique string identifier.</span></span> <span data-ttu-id="253aa-141">Les droits définis par WCF sont définis dans la <xref:System.IdentityModel.Claims.Rights> classe.</span><span class="sxs-lookup"><span data-stu-id="253aa-141">The rights that are defined by WCF are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="253aa-142">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.</span><span class="sxs-lookup"><span data-stu-id="253aa-142">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="253aa-143">L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/complexcustomclaim`, un type de ressource personnalisé `MyResourceType` et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="253aa-143">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a><span data-ttu-id="253aa-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="253aa-144">Example</span></span>  
 <span data-ttu-id="253aa-145">L'exemple de code suivant montre comment créer une revendication personnalisée avec un type de ressource primitif et un type de ressource non primitif.</span><span class="sxs-lookup"><span data-stu-id="253aa-145">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="253aa-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="253aa-146">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="253aa-147">Gestion des revendications et autorisation avec le modèle d'identité</span><span class="sxs-lookup"><span data-stu-id="253aa-147">Managing Claims and Authorization with the Identity Model</span></span>](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
