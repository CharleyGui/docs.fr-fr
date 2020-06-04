---
title: Résolution à liaison tardive ; des erreurs d’exécution peuvent se produire
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: f1dc656a09eee05080356892b280a79505f3b9cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397348"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Résolution à liaison tardive ; des erreurs d’exécution peuvent se produire
Un objet est affecté à une variable déclarée comme étant du [type de données Object](../data-types/object-data-type.md).  
  
 Quand vous déclarez une variable en tant que `Object` , le compilateur doit exécuter une *liaison tardive*, ce qui entraîne des opérations supplémentaires au moment de l’exécution. Cela expose également votre application à de potentielles erreurs d’exécution. Par exemple, si vous assignez un <xref:System.Windows.Forms.Form> à la `Object` variable, puis essayez d’accéder à la <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> propriété, le runtime lève une, <xref:System.MemberAccessException> car la <xref:System.Windows.Forms.Form> classe n’expose pas de `NameTable` propriété.  
  
 Si vous déclarez la variable comme étant d’un type spécifique, le compilateur peut effectuer une *liaison précoce* au moment de la compilation. Cela permet d’améliorer les performances, de contrôler l’accès aux membres du type spécifique et d’améliorer la lisibilité de votre code.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42017  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si possible, déclarez la variable comme étant d’un type spécifique.  
  
## <a name="see-also"></a>Voir aussi

- [Liaison précoce et tardive](../../programming-guide/language-features/early-late-binding/index.md)
- [Déclaration des variables objets](../../programming-guide/language-features/variables/object-variable-declaration.md)
