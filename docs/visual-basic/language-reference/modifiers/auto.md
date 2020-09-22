---
title: Auto
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 799a7320b701384dc5f4b4b46fef8544f6b15b02
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875508"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)

Spécifie que Visual Basic doit marshaler des chaînes d’après les règles de .NET Framework en fonction du nom externe de la procédure externe déclarée.  
  
 Quand vous appelez une procédure définie à l’extérieur de votre projet, le compilateur Visual Basic n’a pas accès aux informations qu’il doit avoir pour appeler correctement la procédure. Ces informations incluent l’emplacement de la procédure, son identification, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise. L' [instruction DECLARE](../statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.  
  
 La `charsetmodifier` partie de l' `Declare` instruction fournit les informations de jeu de caractères pour le marshaling des chaînes lors d’un appel à la procédure externe. Cela affecte également la manière dont Visual Basic recherche le nom de la procédure externe dans le fichier externe. Le `Auto` modificateur spécifie que Visual Basic doit marshaler les chaînes en fonction des règles de .NET Framework, et qu’il doit déterminer le jeu de caractères de base de la plateforme d’exécution et éventuellement modifier le nom de la procédure externe en cas d’échec de la recherche initiale. Pour plus d’informations, consultez « Jeux de caractères » dans l' [instruction DECLARE](../statements/declare-statement.md).  
  
 Si aucun modificateur de jeu de caractères n’est spécifié, `Ansi` est la valeur par défaut.  
  
## <a name="remarks"></a>Notes  

 Le `Auto` modificateur peut être utilisé dans ce contexte :  
  
 [Declare Statement](../statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Notes de développement Smart Device  

 Ce mot clé n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi

- [Caractères](ansi.md)
- [Unicode](unicode.md)
- [Mots clés](../keywords/index.md)
