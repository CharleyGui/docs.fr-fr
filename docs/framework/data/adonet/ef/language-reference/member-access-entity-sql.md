---
title: . (Accès aux membres) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 8e63caba9e9efb91d5c4629b9da0b1feca905ace
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319645"
---
# <a name="-member-access-entity-sql"></a>. (Accès aux membres) (Entity SQL)
L’opérateur point (.) est l’opérateur d’accès aux membres [!INCLUDE[esql](../../../../../../includes/esql-md.md)]. L'opérateur d'accès aux membres permet de produire la valeur d'une propriété ou d'un champ d'une instance de type de modèle conceptuel structurel.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Instance d'un type de modèle conceptuel structurel.  
  
 `identifier`  
 Propriété ou champ appartenant à une instance d'objet.  
  
## <a name="remarks"></a>Notes  
 L'opérateur point (.) peut être utilisé pour extraire les champs d'un enregistrement, de la même manière que l'on extrait les propriétés d'un type complexe ou d'un type d'entité. Par exemple, si n de type Nom est membre du type Personne et que p est une instance du type Personne, alors p.n est une expression d'accès aux membres valide qui produit une valeur de type Nom.  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a>Voir aussi

- [Référence Entity SQL](entity-sql-reference.md)
