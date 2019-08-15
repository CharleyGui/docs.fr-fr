---
title: 'Procédure : hériter de formulaires à l’aide de la boîte de dialogue Sélecteur d’héritage'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 9382f1bf890fb5a886cf547d9b1e9b3031c12eb6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039993"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker"></a>Procédure : Hériter des formulaires à l’aide du sélecteur d’héritage

Le moyen le plus simple d’hériter d’un formulaire ou d’un autre objet consiste à utiliser la boîte de dialogue **Sélecteur d’héritage**. Avec elle, vous pouvez tirer parti du code ou des interfaces utilisateur que vous avez déjà créés dans d'autres solutions.

> [!NOTE]
> Pour hériter d’un formulaire avec la boîte de dialogue **Sélecteur d’héritage**, il faut que le projet contenant ce formulaire ait été intégré à un fichier exécutable ou une DLL. Pour générer le projet, choisissez **Générer la solution** dans le menu **Générer**.

## <a name="create-a-windows-form-by-using-the-inheritance-picker"></a>Créer un Windows Form à l’aide du sélecteur d’héritage

1. Dans Visual Studio, dans le menu **projet** , choisissez **Ajouter un formulaire Windows**.

   La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.

2. Effectuez une recherche dans le modèle de **formulaire hérité** à partir de SearchBox ou en cliquant sur la catégorie **Windows Forms** , sélectionnez-la, puis nommez-la dans la zone **nom** . Cliquez sur le bouton **Ajouter** pour continuer.

   La boîte de dialogue **Sélecteur d’héritage** s’ouvre. Si le projet actuel contient déjà des formulaires, ces derniers sont affichés dans la boîte de dialogue **Sélecteur d’héritage**.

3. Pour hériter d’un formulaire dans un autre assembly, cliquez sur le bouton **Parcourir**.

4. Dans la boîte de dialogue **Sélectionner un fichier qui contient un composant duquel hériter**, naviguez jusqu’au projet contenant le formulaire ou le module souhaité.

5. Cliquez sur le nom du fichier .exe ou .dll pour le sélectionner, puis cliquez sur le bouton **Ouvrir**.

   Cela vous ramène à la boîte de dialogue **Sélecteur d’héritage**, où figure désormais le composant à côté du projet dans lequel il se trouve.

6. Sélectionnez le composant.

   Dans l’**Explorateur de solutions**, le composant est ajouté à votre projet. S’il possède une interface utilisateur, les contrôles qui font partie du formulaire hérité sont marqués d’un glyphe (![capture d’écran de l’Visual Basic](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)symbole d’héritage) et, lorsqu’ils sont sélectionnés, d’une bordure indiquant le niveau de sécurité du contrôle sur le forme superclassée. Les comportements qui correspondent aux différents niveaux de sécurité sont répertoriés dans le tableau ci-dessous.

    |Niveau de sécurité du contrôle|Interaction disponible via le Concepteur et l'Éditeur de code avec le formulaire hérité|
    |-------------------------------|--------------------------------------------------------------------------------|
    |Public|Bordure standard avec poignées de redimensionnement : le contrôle peut-être être dimensionné et déplacé. Le contrôle est accessible en interne par la classe qui le déclare et en externe par d'autres classes.|
    |Protected|Bordure standard avec poignées de redimensionnement : le contrôle peut-être être dimensionné et déplacé. Le contrôle est accessible en interne par la classe qui le déclare et par toute classe qui hérite de la classe parente, mais il n'est pas être accessible aux classes externes.|
    |Protected Internal (Protected Friend en Visual Basic)|Bordure standard avec poignées de redimensionnement : le contrôle peut-être être dimensionné et déplacé. Le contrôle est accessible en interne par la classe qui le déclare, par toute classe qui hérite de la classe parente et par d'autres membres de l'assembly qui le contient.|
    |Internal (Friend en Visual Basic)|Bordure standard sans poignée de redimensionnement, affichée sur le formulaire, propriétés visibles dans la fenêtre **Propriétés**. Toutefois, tous les aspects du contrôle sont considérés en lecture seule. Vous ne pouvez pas déplacer ou dimensionner le contrôle, ni modifier ses propriétés. Si le contrôle est un conteneur d'autres contrôles, comme une zone de groupe, vous ne pouvez pas ajouter de nouveaux contrôles ou supprimer des contrôles existants, même s'ils sont publics. Le contrôle est accessible uniquement par les autres membres de l'assembly qui le contient.|
    |Private|Bordure standard sans poignée de redimensionnement, affichée sur le formulaire, propriétés visibles dans la fenêtre **Propriétés**. Toutefois, tous les aspects du contrôle sont considérés en lecture seule. Vous ne pouvez pas déplacer ou dimensionner le contrôle, ni modifier ses propriétés. Si le contrôle est un conteneur d'autres contrôles, comme une zone de groupe, vous ne pouvez pas ajouter de nouveaux contrôles ou supprimer des contrôles existants, même s'ils sont publics. Le contrôle est accessible uniquement par la classe qui le déclare.|

     Pour plus d’informations sur la façon de modifier l’apparence d’un formulaire de base, consultez [Conséquences de la modification de l’aspect d’un formulaire de base](effects-of-modifying-base-form-appearance.md).

    > [!NOTE]
    > Quand vous combinez des contrôles et des composants hérités avec des contrôles et des composants standard sur des Windows Forms, vous pouvez rencontrer des conflits avec l'ordre de plan. Vous pouvez corriger ce problème en modifiant l’ordre de plan. Pour cela, cliquez dans le menu **Format**, pointez sur **Ordre**, puis cliquez sur **Mettre au premier plan** ou **Mettre à l’arrière-plan**. Pour plus d’informations sur l’ordre de plan des contrôles, [consultez Procédure: Objets de couche sur](../controls/how-to-layer-objects-on-windows-forms.md)Windows Forms.

## <a name="see-also"></a>Voir aussi

- [Inherits (instruction)](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [Conséquences de la modification de l’aspect d’un formulaire de base](effects-of-modifying-base-form-appearance.md)
- [Héritage visuel des Windows Forms](windows-forms-visual-inheritance.md)
