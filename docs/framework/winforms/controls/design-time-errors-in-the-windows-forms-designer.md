---
title: Erreurs au moment du design dans le Concepteur Windows Forms
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015969"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Erreurs au moment du design dans le Concepteur Windows Forms

Cette rubrique explique la signification et l’utilisation de la liste d’erreurs au moment du design qui apparaît dans Visual Studio lorsque le chargement du Concepteur Windows Forms échoue. Si cette liste d’erreurs s’affiche, ne l’interprétez pas comme un bogue du concepteur, mais comme une aide vous permettant de corriger les erreurs dans votre code.

Avoir une connaissance élémentaire de cette liste d’erreurs vous aidera à déboguer vos applications en vous fournissant des informations détaillées sur les erreurs et en suggérant des solutions potentielles.

## <a name="the-design-time-error-list-interface"></a>Interface de liste d’erreurs au moment du design

Si le Concepteur Windows Forms ne parvient pas à se charger, une liste d’erreurs apparaît dans le concepteur. Les erreurs sont regroupées en plusieurs catégories. Par exemple, si vous avez quatre instances de variables non déclarées, celles-ci seront regroupées dans la même catégorie d’erreur. Chaque catégorie d’erreur comprend une brève description qui résume l’erreur.

Vous pouvez développer ou réduire une catégorie d’erreur en cliquant sur l’en-tête de la catégorie d’erreur ou en cliquant sur le chevron développer/réduire. Lorsque vous développez une catégorie d’erreur, l’aide supplémentaire suivante s’affiche :

- Instances de cette erreur.

- Aide sur cette erreur.

- Publications du forum sur cette erreur.

### <a name="instances-of-this-error"></a>Instances de cette erreur

L’aide supplémentaire liste toutes les instances de l’erreur dans le projet en cours. De nombreuses erreurs comprennent un emplacement exact au format suivant : *[nom du projet]* *[nom du formulaire]* Ligne : *[numéro de ligne]* Colonne : *[numéro de colonne]* . Le lien **Accéder au code** vous conduit à l’endroit où l’erreur se produit dans votre code.

Si une pile d’appels est associée à l’erreur, vous pouvez cliquer sur le lien **Afficher la pile des appels**, qui développe davantage l’erreur pour afficher la pile des appels. Examiner la pile peut permettre d’obtenir des informations de débogage utiles. Par exemple, vous pouvez suivre les fonctions appelées avant que l’erreur ne se produise. La pile des appels est sélectionnable ; vous pouvez donc la copier et l’enregistrer.

> [!NOTE]
> En Visual Basic, la liste d’erreurs au moment du design n’affiche pas plus d’une erreur, mais peut afficher plusieurs instances de la même erreur. En Visual C++, les erreurs n’ont pas de lien Accéder au code ou de lien vers les numéros de ligne.

### <a name="forum-posts-about-this-error"></a>Publications de forum sur cette erreur

L’aide supplémentaire comprend un lien vers des publications de Forum relatives à l’erreur. La recherche dans les forums est effectuée en fonction de la chaîne du message d’erreur. Vous pouvez également essayer d’effectuer une recherche sur les forums suivants:

- [Forum Concepteur Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [Forum Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a>Ignorer et continuer

Vous pouvez choisir d’ignorer l’erreur et de continuer à charger le concepteur. Cette action peut entraîner un comportement inattendu. Par exemple, il est possible que les contrôles n’apparaissent pas sur l’aire de conception.

## <a name="see-also"></a>Voir aussi

- [Dépannage du développement au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Dépannage de la création de contrôles et de composants](troubleshooting-control-and-component-authoring.md)
- [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md)
- [Messages d’erreur du Concepteur Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
