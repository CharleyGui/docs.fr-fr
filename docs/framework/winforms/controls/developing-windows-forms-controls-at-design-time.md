---
title: Développer des contrôles au moment du design
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dac049ea6a51037daa0e23dc93476e4410b2df06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745982"
---
# <a name="develop-windows-forms-controls-at-design-time"></a>Développer des contrôles Windows Forms au moment du design

Pour les auteurs de contrôles, le .NET Framework fournit une multitude de technologies de création de contrôles. Les auteurs ne sont plus contraints de concevoir des contrôles composites qui agissent en tant que collection de contrôles préexistants. À travers l’héritage, vous pouvez créer vos propres contrôles à partir de contrôles composites ou de contrôles Windows Forms préexistants. Vous pouvez également concevoir vos propres contrôles qui implémentent un dessin personnalisé. Ces options permettent une grande souplesse dans la conception et les fonctionnalités de l’interface visuelle. Pour tirer parti de ces fonctionnalités, vous devez bien connaître les concepts de la programmation orientée objet.

> [!NOTE]
> Il n’est pas nécessaire d’avoir une compréhension approfondie de l’héritage, mais il peut être utile de faire référence aux [notions de base de l’héritage (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).

Si vous voulez créer des contrôle personnalisés à utiliser sur des Web Forms, consultez [Développement de contrôles serveur ASP.NET personnalisés](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="in-this-section"></a>Dans cette section

[Procédure pas à pas : création d’un contrôle composite](walkthrough-authoring-a-composite-control-with-visual-csharp.md)\
Montre comment créer un contrôle composite simple dans C#.

[Procédure pas à pas : héritage d’un contrôle de Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)\
Montre comment créer un contrôle Windows Forms simple à l’aide de l’héritage dans C#.

[Procédure pas à pas : exécution de tâches courantes à l’aide de balises actives sur des contrôles Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)\
Montre comment utiliser la fonctionnalité de balise active sur les contrôles Windows Forms.

[Procédure pas à pas : sérialisation de collections de types standard avec DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)\
Montre comment utiliser l’attribut <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> pour sérialiser une collection.

[Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)\
Montre comment déboguer le comportement au moment du design de votre contrôle personnalisé.

[Procédure pas à pas : création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md)\
Montre comment intégrer étroitement un contrôle composite dans l’environnement de conception.

[Comment : créer des contrôles pour des Windows Forms](how-to-author-controls-for-windows-forms.md)\
Fournit une vue d’ensemble des considérations pour l’implémentation d’un contrôle Windows Forms.

[Comment : créer des contrôles composites](how-to-author-composite-controls.md)\
Montre comment créer un contrôle en héritant d’un contrôle composite.

[Comment : hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)\
Fournit une vue d’ensemble de la procédure de création d’un contrôle composite.

[Comment : hériter de contrôles Windows Forms existants](how-to-inherit-from-existing-windows-forms-controls.md)\
Montre comment créer un contrôle étendu en héritant de la classe de contrôle <xref:System.Windows.Forms.Button>.

[Comment : hériter de la classe du contrôle](how-to-inherit-from-the-control-class.md)\
Fournit une vue d’ensemble de la création d’un contrôle étendu.

[Comment : aligner un contrôle sur les bords des formulaires au moment du Design](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)\
Montre comment utiliser la propriété <xref:System.Windows.Forms.Control.Dock%2A> pour aligner votre contrôle sur le bord du formulaire qu’il occupe.

[Comment : afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)\
Montre la procédure d’installation de votre contrôle afin qu’il apparaisse dans la boîte de dialogue **Personnaliser la boîte à outils**.

[Comment : fournir une bitmap de boîte à outils pour un contrôle](how-to-provide-a-toolbox-bitmap-for-a-control.md)\
Montre comment utiliser la <xref:System.Drawing.ToolboxBitmapAttribute> pour afficher une icône en regard de votre contrôle personnalisé dans la **boîte à outils**.

[Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md)\
Montre comment utiliser le **conteneur de test UserControl** pour tester le comportement d’un contrôle composite.

[Erreurs au moment du design dans le Concepteur Windows Forms](design-time-errors-in-the-windows-forms-designer.md)\
Explique la signification et l’utilisation de la liste d’erreurs au moment du design qui apparaît dans Microsoft Visual Studio en cas d’échec du chargement du Concepteur Windows Forms.

[Dépannage de la création de contrôles et de composants](troubleshooting-control-and-component-authoring.md)\
Montre comment diagnostiquer et résoudre les problèmes courants qui peuvent se produire quand vous créez un composant ou un contrôle personnalisé.

## <a name="reference"></a>Reference

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a>Rubriques connexes

[Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)\
Explique comment créer vos propres contrôles personnalisés avec le .NET Framework.

[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)\
Présente le common language runtime, qui est conçu pour simplifier la création et l’utilisation des composants. Un aspect important de cette simplification est l’interopérabilité améliorée entre les composants écrits à l’aide de différents langages de programmation. La Common Language Specification (CLS) permet de créer des outils et composants fonctionnant avec plusieurs langages de programmation.

[Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)\
Décrit comment activer l’affichage de votre composant ou de votre contrôle dans la boîte de dialogue **Personnaliser la boîte à outils**.
