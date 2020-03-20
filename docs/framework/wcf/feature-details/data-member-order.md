---
title: Classement des membres de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 2a5d7430953bdc31644e92b9207cd2865209cce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185195"
---
# <a name="data-member-order"></a>Classement des membres de données
Dans certaines applications, il peut s'avérer utile de connaître l'ordre dans lequel les données émanant des divers membres de données sont envoyées ou l'ordre selon lequel leur réception est attendue (il peut, par exemple s'agir de l'ordre dans lequel les données apparaissent dans le langage XML sérialisé). Dans certains cas, la modification de cet ordre peut s'avérer nécessaire. Cette rubrique contient des explications sur les règles régissant ces types de classements.  
  
## <a name="basic-rules"></a>Règles de base  
 Les règles de base concernant le classement des données sont notamment :  
  
- Si un type de contrat de données fait partie d'une hiérarchie d'héritage, les membres de données des types de base de ce type sont toujours classés en premier.  
  
- Viennent ensuite, par ordre alphabétique, les membres de données du type en cours dont la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> de l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> n'est pas définie.  
  
- Viennent ensuite tous les membres de données dont la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> de l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> est définie. Ils sont d'abord classés en fonction de la valeur de la propriété `Order`, puis par ordre alphabétique si plusieurs membres ont une certaine valeur `Order`. Les valeurs de classement peuvent être ignorées.  
  
 L'ordre alphabétique est établi par l'appel de la méthode <xref:System.String.CompareOrdinal%2A>.  
  
## <a name="examples"></a>Exemples  
 Prenons le code suivant.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Le langage XML généré ressemble au langage suivant.  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>
</DerivedType>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Data Contract Equivalence](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
