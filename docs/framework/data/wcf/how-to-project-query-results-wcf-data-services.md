---
title: 'Procédure : Résultats de la requête de projet (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: 758bb01764fcfe195d4f940705316e7579be95ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780005"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>Procédure : Résultats de la requête de projet (WCF Data Services)
La projection fournit un mécanisme permettant de réduire la quantité de données retournées par une requête en spécifiant que seules certaines propriétés d'une entité doivent être retournées dans la réponse. Vous pouvez effectuer des projections sur les résultats d' [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] une requête soit à l' `$select` aide de l’option de requête, soit à l’aide de la clause [Select](../../../csharp/language-reference/keywords/select-clause.md) ([Select](../../../visual-basic/language-reference/queries/select-clause.md) dans Visual Basic) dans une requête LINQ. Pour plus d’informations, consultez [interrogation du service de données](querying-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre une requête LINQ qui projette des entités Customers dans un nouveau type CustomerAddress, qui contient uniquement des propriétés spécifiques à l'adresse ainsi que la propriété d'identité. Cette classe `CustomerAddress` est définie sur le client et est attribuée de sorte que la bibliothèque cliente puisse le reconnaître comme un type d'entité.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre une requête LINQ qui projette les entités Customers renvoyées dans un nouveau type CustomerAddressNonEntity, qui contient uniquement des propriétés spécifiques à l'adresse et aucune propriété d'identité. Cette classe `CustomerAddressNonEntity` est définie sur le client et n'est pas attribuée comme un type d'entité.  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les définitions des `CustomerAddress` types et `CustomerAddressNonEntity` utilisés dans les exemples précédents.  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
