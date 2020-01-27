---
title: Erreurs au moment du design dans le Concepteur Windows Forms
titleSuffix: ''
ms.date: 09/09/2019
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a39c76d011c6d129f91647fabe3f129245b9466
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746087"
---
# <a name="windows-forms-designer-error-page"></a>Page d’erreur Concepteur Windows Forms

Si le Concepteur Windows Forms ne parvient pas à se charger en raison d’une erreur dans votre code, dans un composant tiers ou ailleurs, une page d’erreur s’affiche à la place du concepteur. Cette page d’erreur ne signifie pas nécessairement un bogue dans le concepteur. Le bogue peut se trouver quelque part dans la page code-behind nommée \<votre >-Form-Name. Designer.cs. Les erreurs apparaissent dans des barres réductibles et jaunes avec un lien pour accéder à l’emplacement de l’erreur sur la page de codes.

![Page d’erreur Concepteur Windows Forms](media/windows-forms-designer-error-page-collapsed.png)

Vous pouvez choisir d’ignorer les erreurs et de continuer à charger le concepteur en cliquant sur **ignorer et continuer**. Cette action peut entraîner un comportement inattendu, par exemple, les contrôles peuvent ne pas apparaître sur l’aire de conception.

## <a name="instances-of-this-error"></a>Instances de cette erreur

Lorsque la barre d’erreur jaune est développée, chaque instance de l’erreur est listée. De nombreux types d’erreurs incluent un emplacement exact au format suivant : *[nom du projet]* *[nom du formulaire]* ligne : *[numéro de ligne]* colonne : *[numéro de colonne]* . Si une pile des appels est associée à l’erreur, vous pouvez cliquer sur le lien **afficher la pile des appels** pour l’afficher. L’examen de la pile des appels peut vous aider à résoudre l’erreur.

![Erreur Concepteur Windows Forms développée](media/windows-forms-designer-error-page-expanded.png)

> [!NOTE]
>
> - Pour les applications Visual Basic, la page d’erreurs au moment du design n’affiche pas plus d’une erreur, mais elle peut afficher plusieurs instances de la même erreur.
> - Pour C++ les applications, les erreurs n’ont pas de liens d’emplacement du code.

## <a name="help-with-this-error"></a>Aide sur cette erreur

Si une rubrique d’aide est disponible pour l’erreur, cliquez sur le lien **aide MSDN** pour accéder directement à la page d’aide de docs.Microsoft.com.

## <a name="forum-posts-about-this-error"></a>Publications de forum sur cette erreur

Cliquez sur le lien **Rechercher les publications relatives à cette erreur dans les forums MSDN** pour accéder aux forums Microsoft Developer Network. Vous souhaiterez peut-être effectuer des recherches spécifiques sur les forums [Concepteur Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner) ou [Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms) .

## <a name="design-time-errors"></a>Erreurs au moment du design

Cette section répertorie certaines des erreurs que vous pouvez rencontrer.

### <a name="identifier-name-is-not-a-valid-identifier"></a>'\<nom d’identificateur > 'n’est pas un identificateur valide

Cette erreur indique que le nom d’un champ, d’une méthode, d’un événement ou d’un objet est incorrect.

### <a name="name-already-exists-in-project-name"></a>'\<name > 'existe déjà dans'\<nom du projet > '

Message d’erreur : «le nom de\<> 'existe déjà dans'\<nom du projet > '. Veuillez entrer un nom unique.»

Vous avez spécifié un nom pour un formulaire hérité qui existe déjà dans le projet. Pour corriger cette erreur, attribuez un nom unique à la forme héritée.

### <a name="toolbox-tab-name-is-not-a-toolbox-category"></a>'\<nom de l’onglet de boîte à outils > 'n’est pas une catégorie de boîte à outils

Un concepteur tiers a tenté d’accéder à un onglet de la boîte à outils qui n’existe pas. Contactez le fournisseur du composant.

### <a name="a-requested-language-parser-is-not-installed"></a>Un analyseur de langage demandé n'est pas installé

Message d’erreur : «un analyseur de langage demandé n’est pas installé. Le nom de l’analyseur de langage est «{0}».

Visual Studio a tenté de charger un concepteur qui est inscrit pour le type de fichier, mais n’a pas pu le faire. Cela est probablement dû à une erreur qui s’est produite pendant l’installation. Contactez le fournisseur de la langue que vous utilisez pour résoudre le problème.

### <a name="a-service-required-for-generating-and-parsing-source-code-is-missing"></a>Un service requis pour la génération et l'analyse du code source est absent

Il s’agit d’un problème avec un composant tiers. Contactez le fournisseur du composant.

### <a name="an-exception-occurred-while-trying-to-create-an-instance-of-object-name"></a>Une exception s’est produite lors de la tentative de création d’une instance de'\<nom d’objet > '

Message d’erreur : « une exception s’est produite lors de la tentative de création d’une instance de «\<nom d’objet > ». L’exception était «\<chaîne d’exception\>».

Un concepteur tiers a demandé que Visual Studio crée un objet, mais l’objet a généré une erreur. Contactez le fournisseur du composant.

### <a name="another-editor-has-document-name-open-in-an-incompatible-mode"></a>«\<nom du document > » est ouvert dans un autre éditeur dans un mode incompatible

Message d’erreur : «\<nom du document > » est ouvert dans un autre éditeur dans un mode incompatible. Fermez l’éditeur et recommencez l’opération.»

Cette erreur se produit si vous essayez d’ouvrir un fichier déjà ouvert dans un autre éditeur. L’éditeur sur lequel le fichier est déjà ouvert est affiché. Pour corriger cette erreur, fermez l’éditeur où le fichier est ouvert, puis réessayez.

### <a name="another-editor-has-made-changes-to-document-name"></a>Un autre éditeur a apporté des modifications à «\<nom du document > »

Fermez et rouvrez le concepteur pour que les modifications prennent effet. Normalement, Visual Studio recharge automatiquement un concepteur une fois les modifications apportées. Toutefois, d’autres concepteurs, tels que des concepteurs de composants tiers, peuvent ne pas prendre en charge le comportement de rechargement. Dans ce cas, Visual Studio vous invite à fermer et à rouvrir manuellement le concepteur.

### <a name="another-editor-has-the-file-open-in-an-incompatible-mode"></a>Le fichier est ouvert dans un autre éditeur dans un mode incompatible

Message d’erreur : «le fichier est ouvert dans un autre éditeur dans un mode incompatible. Fermez l’éditeur et recommencez l’opération.»

Ce message est semblable à « l’ouverture d’un autre éditeur est «\<nom du document > » dans un mode incompatible», mais Visual Studio ne peut pas déterminer le nom du fichier. Pour corriger cette erreur, fermez l’éditeur où le fichier est ouvert, puis réessayez.

### <a name="array-rank-rank-in-array-is-too-high"></a>Le rang du tableau'\<rang dans le tableau > 'est trop élevé

Visual Studio ne prend en charge que les tableaux à une seule dimension dans le bloc de code analysé par le concepteur. Les tableaux multidimensionnels sont valides à l’extérieur de cette zone.

### <a name="assembly-assembly-name-could-not-be-opened"></a>Impossible d’ouvrir l’assembly'\<le nom de l’assembly > '

Message d’erreur : « assembly »\<nom de l’assembly >» n’a pas pu être ouvert. Vérifiez que le fichier existe toujours.»

Ce message d’erreur se produit lorsque vous essayez d’ouvrir un fichier qui n’a pas pu être ouvert. Vérifiez que le fichier existe et qu’il s’agit d’un assembly valide.

### <a name="bad-element-type-this-serializer-expects-an-element-of-type-type-name"></a>Type d’élément incorrect. Ce sérialiseur attend un élément de type'\<nom de type > '

Il s’agit d’un problème avec un composant tiers. Contactez le fournisseur du composant.

### <a name="cannot-access-the-visual-studio-toolbox-at-this-time"></a>Impossible d'accéder actuellement à la boîte à outils Visual Studio

Visual Studio a effectué un appel à la boîte à outils, qui n’était pas disponible. Si vous voyez cette erreur, si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-bind-an-event-handler-to-the-event-name-event-because-it-is-read-only"></a>Impossible de lier un gestionnaire d’événements à l’événement’nom de l’événement\<> ', car il est en lecture seule

Cette erreur se produit le plus souvent lorsque vous essayez de connecter un événement à un contrôle hérité d’une classe de base. Si la variable membre du contrôle est privée, Visual Studio ne peut pas connecter l’événement à la méthode. Des événements supplémentaires ne peuvent pas être liés à des contrôles hérités en privé.

### <a name="cannot-create-a-method-name-for-the-requested-component-because-it-is-not-a-member-of-the-design-container"></a>Impossible de créer un nom de méthode pour le composant demandé car il n'est pas membre du conteneur de design

Visual Studio a essayé d’ajouter un gestionnaire d’événements à un composant qui n’a pas de variable membre dans le concepteur. Contactez le fournisseur du composant.

### <a name="cannot-name-the-object-name-because-it-is-already-named-name"></a>Impossible de nommer l’objet « nom\<> », car il est déjà nommé «\<name > »

Il s’agit d’une erreur interne dans le sérialiseur Visual Studio. Elle indique que le sérialiseur a tenté de nommer un objet deux fois, ce qui n’est pas pris en charge. Si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="cannot-remove-or-destroy-inherited-component-component-name"></a>Impossible de supprimer ou de détruire le composant hérité'\<le nom du composant > '

Les contrôles hérités sont sous la propriété de leur classe qui hérite. Les modifications apportées au contrôle hérité doivent être apportées dans la classe d’origine du contrôle. Par conséquent, vous ne pouvez pas le renommer ou le détruire.

### <a name="category-toolbox-tab-name-does-not-have-a-tool-for-class-class-name"></a>La catégorie'\<nom de l’onglet de boîte à outils > 'n’a pas d’outil pour la classe'\<nom de classe > '

Le concepteur a tenté de faire référence à une classe sur un onglet de boîte à outils particulier, mais la classe n’existe pas. Contactez le fournisseur du composant.

### <a name="class-class-name-has-no-matching-constructor"></a>La classe'\<Class Name > 'n’a pas de constructeur correspondant

Un concepteur tiers a demandé à Visual Studio de créer un objet avec des paramètres particuliers dans le constructeur qui n’existe pas. Contactez le fournisseur du composant.

### <a name="code-generation-for-property-property-name-failed"></a>Échec de la génération de code pour la propriété « nom de la propriété\<> »

Il s’agit d’un wrapper générique pour une erreur. La chaîne d’erreur accompagnant ce message donne plus de détails sur le message d’erreur et comporte un lien vers une rubrique d’aide plus spécifique. Pour corriger cette erreur, résolvez l’erreur spécifiée dans le message d’erreur ajouté à cette erreur.

### <a name="component-component-name-did-not-call-containeradd-in-its-constructor"></a>Le composant'\<nom du composant > 'n’a pas appelé Container. Add () dans son constructeur

Il s’agit d’une erreur dans le composant que vous venez de charger ou de placer dans le formulaire. Elle indique que le composant ne s’est pas ajouté à son contrôle conteneur (qu’il s’agisse d’un autre contrôle ou d’un formulaire). Le concepteur continuera de fonctionner, mais il peut y avoir des problèmes avec le composant au moment de l’exécution.

Pour corriger l’erreur, contactez le fournisseur du composant. Ou, s’il s’agit d’un composant que vous avez créé, appelez la méthode `IContainer.Add` dans le constructeur du composant.

### <a name="component-name-cannot-be-empty"></a>Le nom du composant ne peut pas être vide

Cette erreur se produit lorsque vous essayez de renommer un composant en une valeur vide.

### <a name="could-not-access-the-variable-variable-name-because-it-has-not-been-initialized-yet"></a>Impossible d’accéder à la variable « nom de la variable\<> », car elle n’a pas encore été initialisée

Cette erreur peut se produire pour deux scénarios. Soit un fournisseur de composants tiers rencontre un problème avec un contrôle ou un composant qu’il a distribué, soit le code que vous avez écrit a des dépendances récursives entre les composants.

Pour corriger cette erreur, assurez-vous que votre code n’a pas de dépendance récursive. S’il ne s’agit pas de ces problèmes, notez le texte exact du message d’erreur et contactez le fournisseur du composant.

### <a name="could-not-find-type-type-name"></a>Impossible de trouver le type'\<nom du type > '

Message d’erreur : « impossible de trouver le type'\<nom du type > ». Assurez-vous que l’assembly qui contient ce type est référencé. Si ce type fait partie de votre projet de développement, assurez-vous que le projet a été généré avec succès.»

Cette erreur s’est produite, car une référence est introuvable. Assurez-vous que le type indiqué dans le message d’erreur est référencé et que tous les assemblys requis par le type sont également référencés. Souvent, le problème est qu’un contrôle de la solution n’a pas été généré. Pour générer, sélectionnez **générer la solution** dans le menu **générer** . Sinon, si le contrôle a déjà été généré, ajoutez une référence manuellement à partir du menu contextuel du dossier **références** ou **Dependencies** dans Explorateur de solutions.

### <a name="could-not-load-type-type-name"></a>Impossible de charger le type'\<nom du type > '

Message d’erreur : « impossible de charger le type'\<nom du type > ». Assurez-vous que l’assembly contenant ce type est ajouté aux références du projet.»

Visual Studio a tenté d’associer une méthode de gestion des événements et n’a pas pu trouver un ou plusieurs types de paramètres pour la méthode. Cela est généralement dû à une référence manquante. Pour corriger cette erreur, ajoutez la référence contenant le type au projet, puis réessayez.

### <a name="could-not-locate-the-project-item-templates-for-inherited-components"></a>Impossible de trouver les modèles des éléments de projet pour les composants hérités

Les modèles pour les formulaires hérités dans Visual Studio ne sont pas disponibles. Si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="delegate-class-class-name-has-no-invoke-method-is-this-class-a-delegate"></a>La classe déléguée'\<Class Name > 'n’a pas de méthode Invoke. Cette classe est-elle un délégué ?

Visual Studio a essayé de créer un gestionnaire d’événements, mais il y a un problème avec le type d’événement. Cela peut se produire si l’événement a été créé par un langage non conforme CLS. Contactez le fournisseur du composant.

### <a name="duplicate-declaration-of-member-member-name"></a>Déclaration de membre'\<member name > 'dupliquée

Cette erreur se produit parce qu’une variable membre a été déclarée deux fois (par exemple, deux contrôles nommés `Button1` sont déclarés dans le code). Les noms doivent être uniques dans les formulaires hérités. En outre, les noms ne peuvent pas différer uniquement par la casse.

### <a name="error-reading-resources-from-the-resource-file-for-the-culture-culture-name"></a>Erreur lors de la lecture des ressources à partir du fichier de ressources pour la culture'\<nom de culture > '

Cette erreur peut se produire si un fichier. resx est incorrect dans le projet.

Pour corriger cette erreur :

1. Cliquez sur le bouton **Afficher tous les fichiers** dans Explorateur de solutions pour afficher les fichiers. resx associés à la solution.
2. Chargez le fichier. resx dans l’éditeur XML en cliquant avec le bouton droit sur le fichier. resx et en choisissant **ouvrir**.
3. Modifiez le fichier. resx manuellement pour résoudre les erreurs.

### <a name="error-reading-resources-from-the-resource-file-for-the-default-culture-culture-name"></a>Erreur lors de la lecture des ressources à partir du fichier de ressources pour la culture par défaut «\<nom de culture > »

Cette erreur peut se produire si un fichier. resx est incorrect dans le projet pour la culture par défaut.

Pour corriger cette erreur :

1. Cliquez sur le bouton **Afficher tous les fichiers** dans Explorateur de solutions pour afficher les fichiers. resx associés à la solution.
2. Chargez le fichier. resx dans l’éditeur XML en cliquant avec le bouton droit sur le fichier. resx et en choisissant **ouvrir**.
3. Modifiez le fichier. resx manuellement pour résoudre les erreurs.

### <a name="failed-to-parse-method-method-name"></a>Impossible d’analyser la méthode'\<le nom de la méthode > '

Message d’erreur : « impossible d’analyser la méthode'\<le nom de la méthode > ». L’analyseur a signalé l’erreur suivante : «\<chaîne d’erreur > ». Recherchez les erreurs potentielles dans le Liste des tâches.»

Il s’agit d’un message d’erreur général pour les problèmes qui surviennent pendant l’analyse. Ces erreurs sont souvent dues à des erreurs de syntaxe. Consultez le Liste des tâches pour obtenir des messages spécifiques relatifs à l’erreur.

### <a name="invalid-component-name-component-name"></a>Nom de composant non valide : '\<nom du composant > '

Vous avez essayé de renommer un composant avec une valeur non valide pour cette langue. Pour corriger cette erreur, nommez le composant de sorte qu’il soit conforme aux règles d’affectation de noms pour cette langue.

### <a name="the-type-class-name-is-made-of-several-partial-classes-in-the-same-file"></a>Le type'\<Class Name > 'est constitué de plusieurs classes partielles dans le même fichier

Lorsque vous définissez une classe dans plusieurs fichiers à l’aide du mot clé [Partial](../../../csharp/language-reference/keywords/partial-type.md) , vous ne pouvez avoir qu’une seule définition partielle dans chaque fichier.

Pour corriger cette erreur, supprimez toutes les définitions partielles de votre classe à partir du fichier.

### <a name="the-assembly-assembly-name-could-not-be-found"></a>L’assembly'\<le nom de l’assembly > 'est introuvable

Message d’erreur : «l’assembly'\<nom de l’assembly > 'est introuvable. Assurez-vous que l’assembly est référencé. Si l’assembly fait partie du projet de développement actuel, assurez-vous que le projet a été généré.»

Cette erreur est semblable à « le type'\<nom de type > 'est introuvable », mais cette erreur se produit généralement en raison d’un attribut de métadonnées. Pour corriger cette erreur, vérifiez que tous les assemblys utilisés par les attributs sont référencés.

### <a name="the-assembly-name-assembly-name-is-invalid"></a>Le nom d’assembly'\<nom d’assembly > 'n’est pas valide

Un composant a demandé un assembly particulier, mais le nom fourni par le composant n’est pas un nom d’assembly valide. Contactez le fournisseur du composant.

### <a name="the-base-class-class-name-cannot-be-designed"></a>La classe de base'\<nom de la classe > 'ne peut pas être conçue

Visual Studio a chargé la classe, mais la classe ne peut pas être conçue, car l’implémenteur de la classe n’a pas fourni de concepteur. Si la classe prend en charge un concepteur, assurez-vous qu’il n’existe aucun problème susceptible de provoquer des problèmes lors de son affichage dans un concepteur, comme des erreurs de compilateur. En outre, assurez-vous que toutes les références à la classe sont correctes et que tous les noms de classe sont correctement orthographiés. Sinon, si la classe n’est pas concevable, modifiez-la en mode Code.

### <a name="the-base-class-class-name-could-not-be-loaded"></a>Impossible de charger la classe de base'\<nom de la classe > '

La classe n’étant pas référencée dans le projet, Visual Studio ne peut pas la charger. Pour corriger cette erreur, ajoutez une référence à la classe dans le projet, puis fermez et rouvrez la fenêtre de Concepteur Windows Forms.

### <a name="the-class-class-name-cannot-be-designed-in-this-version-of-visual-studio"></a>Impossible de concevoir la classe «\<Class Name > » dans cette version de Visual Studio

Le concepteur de ce contrôle ou composant ne prend pas en charge les mêmes types que Visual Studio. Contactez le fournisseur du composant.

### <a name="the-class-name-is-not-a-valid-identifier-for-this-language"></a>Le nom de la classe n'est pas un identificateur valide pour ce langage

Le code source créé par l’utilisateur a un nom de classe qui n’est pas valide pour la langue utilisée. Pour corriger cette erreur, nommez la classe de façon à ce qu’elle soit conforme aux spécifications de langue.

### <a name="the-component-cannot-be-added-because-it-contains-a-circular-reference-to-reference-name"></a>Impossible d’ajouter le composant, car il contient une référence circulaire à «\<nom de référence > »

Vous ne pouvez pas ajouter un contrôle ou un composant à lui-même. Cela peut également se produire s’il existe du code dans la méthode InitializeComponent d’un formulaire (par exemple, Form1) qui crée une autre instance de Form1.

### <a name="the-designer-cannot-be-modified-at-this-time"></a>Le concepteur ne peut pas être modifié actuellement

Cette erreur se produit lorsque le fichier dans l’éditeur est marqué en lecture seule. Assurez-vous que le fichier n’est pas marqué en lecture seule et que l’application n’est pas en cours d’exécution.

### <a name="the-designer-could-not-be-shown-for-this-file-because-none-of-the-classes-within-it-can-be-designed"></a>Le concepteur n'a pas pu être affiché pour ce fichier, car aucune des classes qu'il contient ne peut être créée

Cette erreur se produit lorsque Visual Studio ne trouve pas de classe de base conforme aux exigences du concepteur. Les formulaires et les contrôles doivent dériver d’une classe de base qui prend en charge les concepteurs. Si vous effectuez une dérivation à partir d’un formulaire ou d’un contrôle hérité, assurez-vous que le projet a été généré.

### <a name="the-designer-for-base-class-class-name-is-not-installed"></a>Le concepteur de la classe de base'\<Class Name > 'n’est pas installé

Visual Studio n’a pas pu charger le concepteur pour la classe. Si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-designer-must-create-an-instance-of-type-type-name-but-it-cant-because-the-type-is-declared-as-abstract"></a>Le concepteur doit créer une instance de type'\<nom de type > ', mais il ne peut pas parce que le type est déclaré comme abstract

Cette erreur s’est produite parce que la classe de base de l’objet passé au concepteur est [abstraite](../../../csharp/language-reference/keywords/abstract.md), ce qui n’est pas autorisé.

### <a name="the-file-could-not-be-loaded-in-the-designer"></a>Le fichier n'a pas pu être chargé dans le concepteur

La classe de base de ce fichier ne prend pas en charge les concepteurs. Pour contourner ce problème, utilisez le mode code pour travailler sur le fichier. Dans Explorateur de solutions, cliquez avec le bouton droit sur le fichier, puis choisissez **afficher le code**.

### <a name="the-language-for-this-file-does-not-support-the-necessary-code-parsing-and-generation-services"></a>Le langage pour ce fichier ne prend pas en charge les services d'analyse et de génération de code nécessaires

Message d’erreur : «la langue de ce fichier ne prend pas en charge les services d’analyse et de génération de code nécessaires. Vérifiez que le fichier que vous ouvrez est membre d’un projet, puis réessayez d’ouvrir le fichier.»

Cette erreur est probablement due à l’ouverture d’un fichier qui se trouve dans un projet qui ne prend pas en charge les concepteurs.

### <a name="the-language-parser-class-class-name-is-not-implemented-properly"></a>La classe de l’analyseur de langage'\<nom de la classe > 'n’est pas implémentée correctement

Message d’erreur : « la classe de l’analyseur de langage'\<le nom de la classe > » n’est pas implémentée correctement. Contactez le fournisseur pour obtenir un module d’analyseur mis à jour.»

Le langage en cours d’utilisation a inscrit une classe de concepteur qui ne dérive pas de la classe de base correcte. Contactez le fournisseur de la langue que vous utilisez.

### <a name="the-name-name-is-already-used-by-another-object"></a>Le nom'\<name > 'est déjà utilisé par un autre objet

Il s’agit d’une erreur interne dans le sérialiseur Visual Studio. Si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-object-object-name-does-not-implement-the-icomponent-interface"></a>L’objet «\<nom d’objet > » n’implémente pas l’interface IComponent

Visual Studio a essayé de créer un composant, mais l’objet créé n’implémente pas l’interface <xref:System.ComponentModel.IComponent>. Contactez le fournisseur du composant pour obtenir un correctif.

### <a name="the-object-object-name-returned-null-for-the-property-property-name-but-this-is-not-allowed"></a>L’objet «\<nom d’objet > » a retourné null pour la propriété «\<nom de la propriété > », mais cela n’est pas autorisé

Certaines propriétés .NET doivent toujours retourner un objet. Par exemple, la collection **Controls** d’un formulaire doit toujours retourner un objet, même s’il n’y a aucun contrôle.

Pour corriger cette erreur, assurez-vous que la propriété spécifiée dans l’erreur n’est pas null.

### <a name="the-serialization-data-object-is-not-of-the-proper-type"></a>Le type de l'objet serialization data n'est pas correct.

Un objet de données fourni par le sérialiseur n’est pas une instance d’un type qui correspond au sérialiseur en cours utilisé. Contactez le fournisseur du composant.

### <a name="the-service-service-name-is-required-but-could-not-be-located"></a>Le service «\<nom du service > » est obligatoire, mais il est introuvable

Message d’erreur : « le service\<nom du service > » est obligatoire, mais il n’a pas pu être localisé. Il se peut qu’il y ait un problème avec votre installation de Visual Studio.»

Un service requis par Visual Studio n’est pas disponible. Si vous essayez de charger un projet qui ne prend pas en charge ce concepteur, utilisez l’éditeur de code pour apporter les modifications dont vous avez besoin. Dans le cas contraire, si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-service-instance-must-derive-from-or-implement-interface-name"></a>L’instance de service doit dériver de ou implémenter'\<nom de l’interface > '

Cette erreur indique qu’un composant ou un concepteur de composants a appelé la méthode **AddService** , qui requiert une interface et un objet, mais que l’objet spécifié n’implémente pas l’interface spécifiée. Contactez le fournisseur du composant.

### <a name="the-text-in-the-code-window-could-not-be-modified"></a>Le texte dans l'éditeur de code n'a pas pu être modifié

Message d’erreur : «le texte de la fenêtre de code n’a pas pu être modifié. Vérifiez que le fichier n’est pas en lecture seule et qu’il y a suffisamment d’espace disque.

Cette erreur se produit lorsque Visual Studio ne peut pas modifier un fichier en raison d’un espace disque ou de problèmes de mémoire, ou si le fichier est marqué en lecture seule.

### <a name="the-toolbox-enumerator-object-only-supports-retrieving-one-item-at-a-time"></a>L'objet énumérateur Toolbox prend en charge la récupération d'un seul élément à la fois

Si vous voyez cette erreur, si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="the-toolbox-item-for-component-name-could-not-be-retrieved-from-the-toolbox"></a>Impossible de récupérer l’élément de boîte à outils pour «\<nom du composant > » à partir de la boîte à outils

Message d’erreur : « impossible de récupérer l’élément de boîte à outils pour'\<nom du composant > » à partir de la boîte à outils. Assurez-vous que l’assembly qui contient l’élément de boîte à outils est correctement installé. L’élément de boîte à outils a déclenché l’erreur suivante : \<chaîne d’erreur >.»

Le composant en question a levé une exception lorsque Visual Studio y a accédé. Contactez le fournisseur du composant.

### <a name="the-toolbox-item-for-toolbox-item-name-could-not-be-retrieved-from-the-toolbox"></a>Impossible de récupérer l’élément de boîte à outils pour'\<nom d’élément de boîte à outils > 'à partir de la boîte à outils

Message d’erreur : « impossible de récupérer l’élément de boîte à outils pour le nom d’élément de boîte à outils\<> » à partir de la boîte à outils. Essayez de supprimer l’élément de la boîte à outils et de le rajouter.»

Cette erreur se produit si les données de l’élément de boîte à outils sont endommagées ou si la version du composant a été modifiée. Essayez de supprimer l’élément de la boîte à outils et de le rajouter.

### <a name="the-type-type-name-could-not-be-found"></a>Le type « nom de type\<> » est introuvable

Message d’erreur : « le type'\<nom du type > » est introuvable. Assurez-vous que l’assembly contenant le type est référencé. Si l’assembly fait partie du projet de développement actuel, assurez-vous que le projet a été généré.»

Lors du chargement du concepteur, Visual Studio n’a pas trouvé de type. Assurez-vous que l’assembly contenant le type est référencé. Si l’assembly fait partie du projet de développement actuel, assurez-vous que le projet a été généré.

### <a name="the-type-resolution-service-may-only-be-called-from-the-main-application-thread"></a>Le service de résolution de type ne peut être appelé qu'à partir du thread d'application principal

Visual Studio a tenté d’accéder aux ressources requises à partir d’un thread incorrect. Cette erreur s’affiche lorsque le code utilisé pour créer le concepteur a appelé le service de résolution de type à partir d’un thread autre que le thread d’application principal. Pour corriger cette erreur, appelez le service à partir du thread approprié ou contactez le fournisseur du composant.

### <a name="the-variable-variable-name-is-either-undeclared-or-was-never-assigned"></a>La variable « nom de la variable\<> » n’est pas déclarée ou n’a jamais été assignée

Le code source a une référence à une variable, telle que **Button1**, qui n’est pas déclarée ou assignée. Si la variable n’a pas été assignée, ce message apparaît comme un avertissement, et non comme une erreur.

### <a name="there-is-already-a-command-handler-for-the-menu-command-menu-command-name"></a>Il existe déjà un gestionnaire de commandes pour la commande de menu «\<nom de la commande de menu > »

Cette erreur se produit si un concepteur tiers ajoute une commande qui a déjà un gestionnaire à la table de commandes. Contactez le fournisseur du composant.

### <a name="there-is-already-a-component-named-component-name"></a>Il existe déjà un composant nommé «\<Component name > »

Message d’erreur : « il existe déjà un composant nommé «\<nom du composant > ». Les composants doivent avoir des noms uniques et les noms ne doivent pas être sensibles à la casse. Un nom ne peut pas non plus être en conflit avec le nom d’un composant dans une classe héritée.»

Ce message d’erreur se produit lorsqu’une modification a été apportée au nom d’un composant dans la Fenêtre Propriétés. Pour corriger cette erreur, assurez-vous que tous les noms de composants sont uniques, qu’ils ne respectent pas la casse et qu’ils ne sont pas en conflit avec les noms des composants des classes héritées.

### <a name="there-is-already-a-toolbox-item-creator-registered-for-the-format-format-name"></a>Un créateur d’élément de boîte à outils est déjà inscrit au format «\<le nom de format > »

Un composant tiers a effectué un rappel à un élément d’un onglet de boîte à outils, mais l’élément contenait déjà un rappel. Contactez le fournisseur du composant.

### <a name="this-language-engine-does-not-support-a-codemodel-with-which-to-load-a-designer"></a>Ce moteur de langage ne prend pas en charge de CodeModel pour charger un concepteur

Ce message est semblable à « le langage de ce fichier ne prend pas en charge les services d’analyse et de génération de code nécessaires », mais ce message implique un problème d’inscription interne. Si vous voyez cette erreur, si vous voyez cette erreur, veuillez consigner un problème en utilisant [signaler un problème](/visualstudio/ide/how-to-report-a-problem-with-visual-studio).

### <a name="type-type-name-does-not-have-a-constructor-with-parameters-of-types-parameter-type-names"></a>Le type'\<nom du type\>'n’a pas de constructeur avec des paramètres de types'\<noms de type de paramètre > '

Visual Studio n’a pas pu trouver un [constructeur](../../../csharp/programming-guide/classes-and-structs/constructors.md) qui avait des paramètres correspondants. Cela peut être le résultat de la fourniture d’un constructeur avec des types autres que ceux qui sont requis. Par exemple, un constructeur **point** peut prendre deux entiers. Si vous avez fourni des valeurs float, cette erreur est générée.

Pour corriger cette erreur, utilisez un autre constructeur ou effectuez un cast explicite des types de paramètres de façon à ce qu’ils correspondent à ceux fournis par le constructeur.

### <a name="unable-to-add-reference-reference-name-to-the-current-application"></a>Impossible d’ajouter la référence'\<le nom de référence > 'à l’application actuelle

Message d’erreur : « impossible d’ajouter une référence'\<nom de référence > » à l’application actuelle. Vérifiez qu’une version différente de'\<nom de référence > 'n’est pas déjà référencée. "

Visual Studio ne peut pas ajouter de référence. Pour corriger cette erreur, vérifiez qu’une autre version de la référence n’est pas déjà référencée.

### <a name="unable-to-check-out-the-current-file"></a>Impossible d'extraire le fichier en cours

Message d’erreur : «impossible d’extraire le fichier actif. Le fichier est peut-être verrouillé ou vous devrez peut-être extraire le fichier manuellement.»

Cette erreur se produit lorsque vous modifiez un fichier actuellement archivé dans le contrôle de code source. En général, Visual Studio affiche la boîte de dialogue d’extraction de fichier afin que l’utilisateur puisse extraire le fichier. Cette fois-ci, le fichier n’a pas été extrait, peut-être en raison d’un conflit de fusion lors de l’extraction. Pour corriger cette erreur, assurez-vous que le fichier n’est pas verrouillé, puis essayez d’extraire le fichier manuellement.

### <a name="unable-to-find-page-named-options-dialog-box-tab-name"></a>Impossible de trouver la page nommée «\<options de la boîte de dialogue Options nom > »

Cette erreur se produit lorsqu’un concepteur de composants demande l’accès à une page à partir de la boîte de dialogue Options en utilisant un nom qui n’existe pas. Contactez le fournisseur du composant.

### <a name="unable-to-find-property-property-name-on-page-options-dialog-box-tab-name"></a>Impossible de trouver la propriété'\<nom de propriété > 'à la page’options de la boîte de dialogue Options\<nom de l’onglet > '

Cette erreur se produit lorsqu’un concepteur de composants demande l’accès à une valeur particulière sur une page à partir de la boîte de dialogue Options, mais que cette valeur n’existe pas. Contactez le fournisseur du composant.

### <a name="visual-studio-cannot-open-a-designer-for-the-file-because-the-class-within-it-does-not-inherit-from-a-class-that-can-be-visually-designed"></a>Visual Studio ne peut pas ouvrir de concepteur pour ce fichier, car la classe qu'il contient n'hérite pas d'une classe qui peut être conçue visuellement

Visual Studio a chargé la classe, mais son concepteur n'a pas pu être chargé. Visual Studio requiert que les concepteurs utilisent la première classe dans un fichier. Pour corriger cette erreur, déplacez le code de la classe afin qu’il corresponde à la première classe dans le fichier, puis rechargez le concepteur.

### <a name="visual-studio-cannot-save-or-load-instances-of-the-type-type-name"></a>Visual Studio ne peut pas enregistrer ou charger les instances du type'\<nom du type > '

Il s’agit d’un problème avec un composant tiers. Contactez le fournisseur du composant.

### <a name="visual-studio-is-unable-to-open-document-name-in-design-view"></a>Visual Studio ne peut pas ouvrir «\<nom du document > » dans Mode Création

Message d’erreur : « Visual Studio ne peut pas ouvrir «\<nom du document > » dans Mode Création. Aucun analyseur n’est installé pour le type de fichier.»

Cette erreur indique que la langue du projet ne prend pas en charge un concepteur et se produit lorsque vous tentez d’ouvrir un fichier dans la boîte de dialogue Ouvrir un fichier ou à partir de Explorateur de solutions. Au lieu de cela, modifiez le fichier en mode Code.

### <a name="visual-studio-was-unable-to-find-a-designer-for-classes-of-type-type-name"></a>Visual Studio n’a pas pu trouver de concepteur pour les classes de type « nom de type\<> »

Visual Studio a chargé la classe, mais la classe ne peut pas être conçue. Au lieu de cela, modifiez la classe en mode Code en cliquant avec le bouton droit sur la classe et en choisissant **afficher le code**.

## <a name="see-also"></a>Voir aussi

- [Développer des contrôles Windows Forms à l’aide du concepteur](developing-windows-forms-controls-at-design-time.md)
- [Forum Concepteur Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)
