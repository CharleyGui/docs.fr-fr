---
title: Fonctions définies par l'utilisateur
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 061e07ba91a1742c90a594bf42f12e64172b2481
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164114"
---
# <a name="user-defined-functions"></a>Fonctions définies par l'utilisateur

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilise des méthodes dans votre modèle objet pour représenter des fonctions définies par l'utilisateur. Vous désignez des méthodes comme des fonctions en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>. Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md).  
  
 Pour éviter une exception <xref:System.InvalidOperationException>, les fonctions définies par l'utilisateur dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] doivent prendre l'une des formes suivantes :  
  
- Fonction encapsulée comme un appel de méthode disposant des attributs de mappage appropriés. Pour plus d’informations, consultez [mappage basé sur les attributs](attribute-based-mapping.md).  
  
- Méthode SQL statique spécifique à [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Fonction prise en charge par une méthode .NET Framework.  
  
 Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code. Les développeurs qui utilisent Visual Studio utilisent généralement le Concepteur Objet Relationnel pour mapper des fonctions définies par l’utilisateur.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Procédure : Utiliser des fonctions scalaires définies par l’utilisateur](how-to-use-scalar-valued-user-defined-functions.md)  
 Décrit comment implémenter une fonction qui retourne des valeurs scalaires.  
  
 [Procédure : Utiliser des fonctions tables définies par l’utilisateur](how-to-use-table-valued-user-defined-functions.md)  
 Décrit comment implémenter une fonction qui retourne des valeurs de table.  
  
 [Procédure : Appeler des fonctions inline définies par l’utilisateur](how-to-call-user-defined-functions-inline.md)  
 Décrit comment passer des appels inline à des fonctions et les différences d'exécution lorsque l'appel est rendu inline.
