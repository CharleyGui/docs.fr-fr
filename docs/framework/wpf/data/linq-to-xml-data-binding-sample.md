---
title: Exemple de liaison de données LINQ to XML
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920936"
---
# <a name="linq-to-xml-data-binding-sample"></a>Exemple de liaison de données LINQ to XML

Cet article décrit l’exemple LinqToXmlDataBinding, une application Windows Presentation Foundation (WPF) qui lie des composants d’interface utilisateur à une source de données XML incorporée.

## <a name="overview"></a>Vue d'ensemble

L’exemple LinqToXmlDataBinding est une application Windows Presentation Foundation (WPF) qui contient C# des fichiers sources XAML et. Un document XML incorporé définit une liste de livres. L’application permet à l’utilisateur d’afficher, d’ajouter, de supprimer et de modifier les entrées de livre.

Il existe deux fichiers sources principaux :

- [L2DBForm.xaml](l2dbform-xaml-source-code.md) contient le code de déclaration XAML pour l’interface utilisateur de la fenêtre principale. Elle contient également une section de ressources de fenêtre qui définit un fournisseur de données et un document XML incorporé pour les listes de livres.

- [L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) contient les méthodes d’initialisation et de gestion d’événements associées à l’interface utilisateur.

La fenêtre principale est composée des quatre sections d'interface utilisateur verticales suivantes :

- **XML** affiche la source XML brute de la liste de livres incorporée.

- **Book List** affiche les entrées de livres au format texte standard et permet à l’utilisateur de sélectionner et de supprimer des entrées.

- **Edit Selected Book** permet à l’utilisateur de modifier les valeurs associées à l’entrée de livre sélectionnée.

- **Add New Book** permet la création d’une nouvelle entrée de livre sur la base des valeurs entrées par l’utilisateur.

## <a name="run-the-sample"></a>Exécuter l’exemple

Cette section montre comment créer et générer le projet LinqToXmlDataBinding dans Visual Studio, et comment exécuter l’application LinqToXmlDataBinding Windows Presentation Foundation (WPF) résultante.

### <a name="create-the-project"></a>Créer le projet

1. Ouvrez Visual Studio et créez une **application WPF** C# nommée **LinqToXmlDataBinding**.

   Le projet doit cibler le .NET Framework 3.5 (ou version ultérieure).

1. Si elles ne sont pas déjà présentes, ajoutez les références de projet pour les assemblys .NET suivants :

    - System.Data
    - System.Data.DataSetExtensions
    - System.Xml
    - System.Xml

1. Générez la solution en appuyant sur **Ctrl**+**Maj**+**B**, puis exécutez-la en appuyant sur **F5**.

   Le projet doit être compilé sans erreur et exécuté en tant qu'application WPF générique.

### <a name="add-code"></a>Ajouter du code

1. Dans l’**Explorateur de solutions**, renommez le fichier source **Window1.xaml** en **L2XDBForm.xaml**.

   Le fichier source dépendant Window1.xaml.cs est automatiquement renommé en L2XDBForm.xaml.cs.

1. Remplacez le code source trouvé dans le fichier **L2XDBForm. Xaml** par le [code source L2DBForm. Xaml](l2dbform-xaml-source-code.md). Utilisez la vue source XAML pour travailler avec ce fichier.

1. De même, remplacez la source dans **L2XDBForm.Xaml.cs** par le [code source L2DBForm.Xaml.cs](l2dbform-xaml-cs-source-code.md).

1. Dans le fichier **app. Xaml**, remplacez toutes les occurrences de la chaîne **Window1. Xaml** par **L2XDBForm. Xaml**.

1. Générez la solution en appuyant sur **Ctrl**+**Maj**+**B**.

### <a name="run-the-app"></a>Exécuter l'application

L’application LinqToXmlDataBinding permet à l’utilisateur d’afficher et de manipuler une liste de livres stockée en tant qu’élément XML incorporé. Exécutez l’application en appuyant sur **F5** (démarrer le débogage) ou **CTRL**+**F5** (exécuter sans débogage).

Une fenêtre de programme avec le titre **WPF Data Binding using LINQ to XML** apparaît.

La partie supérieure de l’interface utilisateur affiche le **code XML** brut qui représente la liste de livres. Il est affiché à l'aide d'un contrôle <xref:System.Windows.Controls.TextBlock> WPF, qui n'autorise pas d'interaction via le clavier ou la souris.

La deuxième section verticale, libellée **Book List**, affiche les livres sous la forme d’une liste ordonnée en texte brut. Elle utilise un contrôle <xref:System.Windows.Controls.ListBox> qui autorise la sélection via la souris ou le clavier.

### <a name="add-and-delete-books"></a>Ajouter et supprimer des livres

Pour ajouter un nouveau livre à la liste, entrez des valeurs dans les contrôles **ID** et **value** <xref:System.Windows.Controls.TextBox> dans la dernière section, **Add New Book**, puis sélectionnez **Add Book**. Le livre est ajouté à la liste dans les listes livre et XML. Ce programme ne valide pas les valeurs d'entrée.

Pour supprimer un livre existant de la liste, sélectionnez-le dans la section **Book List** , puis sélectionnez **Remove selected Book**. L’entrée de livre est supprimée du livre et des listes de sources XML brutes.

### <a name="edit-a-book-entry"></a>Modifier une entrée de livre

1. Sélectionnez l’entrée de livre dans la deuxième section **Book List**.

   Ses valeurs actuelles s’affichent dans la section **modifier le livre sélectionné** .

1. Modifiez les valeurs à l'aide du clavier. Dès que l’un ou l’autre <xref:System.Windows.Controls.TextBox> contrôle perd le focus, les modifications sont propagées automatiquement à la source XML et aux listes de livres.
