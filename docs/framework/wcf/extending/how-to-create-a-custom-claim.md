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
# <a name="how-to-create-a-custom-claim"></a>Comment : créer une revendication personnalisée
L’infrastructure Identity Model de windows Communication Foundation (WCF) fournit un ensemble de types <xref:System.IdentityModel.Claims.Claim> et de droits intégrés de réclamation avec les fonctions d’aide pour créer des instances avec ces types et droits. Ces réclamations intégrées sont conçues pour modéliser les informations trouvées dans les types d’identification des clients que WCF prend en charge par défaut. Dans la plupart des cas, les revendications intégrées sont suffisantes ; toutefois, certaines applications peuvent requérir des revendications personnalisées. Une revendication comporte trois volets : le type de revendication, la ressource à laquelle la revendication s'applique et le droit revendiqué sur cette ressource. Cette rubrique décrit comment créer une revendication personnalisée.  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a>Pour créer une revendication personnalisée basée sur un type de données primitif  
  
1. Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.  
  
    1. Choisissez une valeur unique pour le type de revendication.  
  
         Le type de revendication est un identificateur de chaîne unique. Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique. Pour une liste de types de réclamations <xref:System.IdentityModel.Claims.ClaimTypes> qui sont définis par WCF, voir la classe.  
  
    2. Choisissez le type de données primitif et la valeur de la ressource.  
  
         Une ressource est un objet. Le type CLR de la ressource peut être une primitive, telle que <xref:System.String> ou <xref:System.Int32>, ou tout type sérialisable. Le type CLR de la ressource doit être sérialisable, parce que les revendications sont sérialisées à divers moments par WCF. Les types primitifs sont sérialisables.  
  
    3. Choisissez un droit qui est défini par WCF ou une valeur unique pour un droit personnalisé.  
  
         Un droit est un identificateur de chaîne unique. Les droits définis par WCF <xref:System.IdentityModel.Claims.Rights> sont définis dans la classe.  
  
         Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.  
  
         L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/simplecustomclaim`, pour une ressource nommée `Driver's License`, et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a>Pour créer une revendication personnalisée basée sur un type de données non primitif  
  
1. Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.  
  
    1. Choisissez une valeur unique pour le type de revendication.  
  
         Le type de revendication est un identificateur de chaîne unique. Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique. Pour une liste de types de réclamations <xref:System.IdentityModel.Claims.ClaimTypes> qui sont définis par WCF, voir la classe.  
  
    2. Choisissez ou définissez un type non primitif sérialisable pour la ressource.  
  
         Une ressource est un objet. Le type CLR de la ressource doit être sérialisable, parce que les revendications sont sérialisées à divers moments par WCF. Les types primitifs sont déjà sérialisables.  
  
         Lorsqu'un nouveau type est défini, appliquez <xref:System.Runtime.Serialization.DataContractAttribute> à la classe. Appliquez également l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à tous les membres du nouveau type qui doivent être sérialisés dans le cadre de la revendication.  
  
         L'exemple de code suivant définit un type de ressource personnalisé nommé `MyResourceType`.  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)]
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]
  
    3. Choisissez un droit qui est défini par WCF ou une valeur unique pour un droit personnalisé.  
  
         Un droit est un identificateur de chaîne unique. Les droits définis par WCF <xref:System.IdentityModel.Claims.Rights> sont définis dans la classe.  
  
         Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.  
  
         L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/complexcustomclaim`, un type de ressource personnalisé `MyResourceType` et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)]
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]
  
## <a name="example"></a> Exemple  
 L'exemple de code suivant montre comment créer une revendication personnalisée avec un type de ressource primitif et un type de ressource non primitif.  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Gestion des revendications et autorisation avec le modèle d'identité](../feature-details/managing-claims-and-authorization-with-the-identity-model.md)
