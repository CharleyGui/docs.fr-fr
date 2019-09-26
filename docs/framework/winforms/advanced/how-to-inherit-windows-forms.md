---
title: 'Procédure : hériter de Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 402386e16687162e25e16e5c30c787f7e721fbba
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306374"
---
# <a name="how-to-inherit-windows-forms"></a>Procédure : hériter de Windows Forms

Créer des Windows Forms en héritant de formulaires de base est un moyen pratique de dupliquer vos efforts sans avoir à recréer entièrement un formulaire chaque fois que vous en avez besoin.

Pour plus d’informations sur l’héritage de formulaires au moment du design à l’aide de la boîte de dialogue **Sélecteur d’héritage** et sur la façon de faire [la distinction visuelle entre les niveaux de sécurité des contrôles hérités, consultez Procédure : Héritez des formulaires à l’aide de](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)la boîte de dialogue Sélecteur d’héritage.

> [!NOTE]
> Pour hériter d’un formulaire, le fichier ou l’espace de noms contenant ce formulaire doit avoir été intégré à un fichier exécutable ou une DLL. Pour générer le projet, choisissez **Générer** dans le menu **Générer**. De plus, une référence à l'espace de noms doit être ajoutée à la classe héritant du formulaire.

## <a name="inherit-a-form-programmatically"></a>Hériter d’un formulaire par programmation

1. Dans votre classe, ajoutez une référence à l'espace de noms contenant le formulaire dont vous voulez hériter.

2. Dans la définition de classe, ajoutez une référence au formulaire à partir duquel hériter. Cette référence doit inclure l'espace de noms qui contient le formulaire, suivi d'un point, puis du nom du formulaire de base proprement dit.

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 Lors de l'héritage de formulaires, n'oubliez pas que des problèmes peuvent survenir car les gestionnaires d'événements peuvent être appelés deux fois (chaque événement étant géré par la classe de base et par la classe héritée). Pour plus d’informations sur la façon d’éviter ce problème, consultez [Dépannage des gestionnaires d’événements hérités dans Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="see-also"></a>Voir aussi

- [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](../../../csharp/language-reference/keywords/using.md)
- [Conséquences de la modification de l’aspect d’un formulaire de base](effects-of-modifying-base-form-appearance.md)
- [Héritage visuel des Windows Forms](windows-forms-visual-inheritance.md)
