---
title: Ansi
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 8dfd830e4c7ed97c8813da4ad310ee59b26f44f8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90868806"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)

Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs American National Standards Institute (ANSI), quel que soit le nom de la procédure externe déclarée.  
  
 Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations dont il a besoin pour appeler correctement la procédure. Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise. L' [instruction DECLARE](../statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 La `charsetmodifier` partie de l' `Declare` instruction fournit les informations de jeu de caractères pour le marshaling des chaînes lors d’un appel à la procédure externe. Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe. Le `Ansi` modificateur spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs ANSI et rechercher la procédure sans modifier son nom au cours de la recherche.  
  
 Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.  
  
## <a name="remarks"></a>Notes  

 Le `Ansi` modificateur peut être utilisé dans ce contexte :  
  
 [Declare Statement](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notes de développement Smart Device  

 Ce mot clé n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Automatique](auto.md)
- [Unicode](unicode.md)
- [Mots clés](../keywords/index.md)
