---
title: Propriétés d’accessibilité sur les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
ms.openlocfilehash: 73d81f5b5f656ed5ef90bdd9b6fe1b3293123f97
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743422"
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a>Propriétés des contrôles Windows Forms que prennent en charge les instructions relatives à l'accessibilité
Les contrôles de la boîte à outils standard pour Windows Forms prennent en charge la plupart des règles d’accessibilité, notamment l’exposition du focus clavier et l’exposition des éléments d’écran.  
  
## <a name="planning-ahead-for-accessibility"></a>Planification à l’avance pour l’accessibilité  
 Les propriétés des contrôles peuvent être utilisées pour prendre en charge d’autres règles d’accessibilité, comme indiqué dans le tableau suivant. En outre, vous devez utiliser des menus pour fournir un accès aux fonctionnalités du programme.  
  
|Control, propriété|Considérations relatives à l’accessibilité|  
|----------------------|--------------------------------------|  
|AccessibleDescription|La description est indiquée dans les aides à l’accessibilité, telles que les lecteurs d’écran. Les aides à l’accessibilité sont des programmes et des dispositifs spécialisés qui aident les personnes handicapées à utiliser plus efficacement les ordinateurs.|  
|AccessibleName|Nom qui sera signalé aux aides d’accessibilité.|  
|AccessibleRole|Décrit l’utilisation de l’élément dans l’interface utilisateur.|  
|TabIndex|Crée un chemin de navigation raisonnable via le formulaire. Il est important que les contrôles sans étiquettes intrinsèques, tels que les zones de texte, soient immédiatement précédés de leur étiquette dans l’ordre de tabulation.|  
|Text|Utilisez le caractère « & » pour créer des clés d’accès. L’utilisation de clés d’accès fait partie intégrante d’un accès clavier documenté aux fonctionnalités.|  
|Font Size|Si la taille de la police n’est pas réglable, elle doit être définie sur 10 points ou plus. Une fois que la taille de police du formulaire est définie, tous les contrôles ajoutés au formulaire par la suite auront la même taille.|  
|ForeColor|Si cette propriété est définie sur la valeur par défaut, les préférences de couleur de l’utilisateur sont utilisées dans le formulaire.|  
|BackColor|Si cette propriété est définie sur la valeur par défaut, les préférences de couleur de l’utilisateur sont utilisées dans le formulaire.|  
|BackgroundImage|Laissez cette propriété vide pour rendre le texte plus lisible.|  
  
## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d'une application Windows accessible](walkthrough-creating-an-accessible-windows-based-application.md)
