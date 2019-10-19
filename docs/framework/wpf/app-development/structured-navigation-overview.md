---
title: Vue d'ensemble de la navigation structurée
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 76330c1228b1f55a5dbaf58a1acd231a391d550c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580512"
---
# <a name="structured-navigation-overview"></a>Vue d'ensemble de la navigation structurée

Le contenu qui peut être hébergé par un [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], un <xref:System.Windows.Controls.Frame> ou un <xref:System.Windows.Navigation.NavigationWindow> est composé de pages qui peuvent être identifiées par des URI (Uniform Resource Identifier) de Pack et qui sont parcourues par des liens hypertexte. La structure des pages et comment elles sont accessibles, tel que défini par des liens hypertexte, porte le nom de topologie de navigation. Une telle topologie convient à différents types d’applications, notamment celles permettant de parcourir des documents. Pour de telles applications, l’utilisateur peut naviguer d’une page à une autre page sans qu’une page ait besoin de savoir quoi que ce soit sur l’autre page.

Toutefois, d’autres types d’applications ont des pages qui ont besoin de savoir quand une navigation parmi les pages a eu lieu. Par exemple, considérez une application de ressources humaines ayant une page pour répertorier tous les employés d’une organisation, la page « Liste des employés ». Cette page pourrait également permettre aux utilisateurs d’ajouter un nouvel employé en cliquant sur un lien hypertexte. En cas de clic sur ce lien, l’utilisateur accède à une page « Ajouter un employé » pour recueillir les détails du nouvel employé et les retourner à la page « Liste des employés » afin de créer le nouvel employé et de mettre à jour la liste. Ce style de navigation s’apparente à l’appel d’une méthode pour effectuer un traitement et retourner une valeur, ce qui porte le nom de programmation structurée. Ce style de navigation est appelé *navigation structurée*.

La classe <xref:System.Windows.Controls.Page> n’implémente pas la prise en charge de la navigation structurée. Au lieu de cela, la classe <xref:System.Windows.Navigation.PageFunction%601> dérive de <xref:System.Windows.Controls.Page> et l’étend avec les constructions de base requises pour la navigation structurée. Cette rubrique montre comment établir une navigation structurée à l’aide de <xref:System.Windows.Navigation.PageFunction%601>.

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>Navigation structurée

Quand une page en appelle une autre dans une navigation structurée, certains ou tous les comportements suivants sont nécessaires :

- La page appelante accède à la page appelée, éventuellement en passant les paramètres exigés par cette dernière.

- La page appelée, quand un utilisateur a fini d’utiliser la page appelante, revient spécifiquement à la page appelante et, éventuellement :

  - Retourne des informations d’état qui décrivent comment la page appelante a été terminée (par exemple, si un utilisateur a appuyé sur un bouton OK ou Annuler)

  - Retourne les données recueillies auprès de l’utilisateur (par exemple, les détails du nouvel employé)

- Quand la page appelante revient à la page appelée, celle-ci est supprimée de l’historique de navigation afin d’isoler une instance d’une page appelée d’une autre.

Ces comportements sont illustrés par la figure suivante :

![Capture d’écran montre le flow entre la page appelante et la page appelée.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

Vous pouvez implémenter ces comportements à l’aide d’un <xref:System.Windows.Navigation.PageFunction%601> comme page appelée.

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>Navigation structurée avec PageFunction

Cette rubrique montre comment implémenter les mécanismes de base de la navigation structurée impliquant une seule <xref:System.Windows.Navigation.PageFunction%601>. Dans cet exemple, un <xref:System.Windows.Controls.Page> appelle une <xref:System.Windows.Navigation.PageFunction%601> pour obtenir une valeur <xref:System.String> de l’utilisateur et la retourner.

### <a name="creating-a-calling-page"></a>Création d’une page appelante

La page qui appelle un <xref:System.Windows.Navigation.PageFunction%601> peut être une <xref:System.Windows.Controls.Page> ou un <xref:System.Windows.Navigation.PageFunction%601>. Dans cet exemple, il s’agit d’un <xref:System.Windows.Controls.Page>, comme indiqué dans le code suivant.

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>Création d’une fonction de page à appeler

Étant donné que la page appelante peut utiliser la page appelée pour collecter et retourner des données de l’utilisateur, <xref:System.Windows.Navigation.PageFunction%601> est implémenté en tant que classe générique dont l’argument de type spécifie le type de la valeur retournée par la page appelée. Le code suivant illustre l’implémentation initiale de la page appelée, à l’aide d’un <xref:System.Windows.Navigation.PageFunction%601>, qui retourne une <xref:System.String>.

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

La déclaration d’un <xref:System.Windows.Navigation.PageFunction%601> est semblable à la déclaration d’un <xref:System.Windows.Controls.Page> avec l’ajout des arguments de type. Comme vous pouvez le constater dans l’exemple de code, les arguments de type sont spécifiés à la fois dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (à l’aide de l’attribut `x:TypeArguments`) et dans le code-behind (à l’aide de la syntaxe d’argument de type générique standard).

Vous n’êtes pas obligé d’utiliser uniquement des classes .NET Framework en tant qu’arguments de type. Un <xref:System.Windows.Navigation.PageFunction%601> peut être appelé pour collecter des données spécifiques au domaine qui sont abstraites en tant que type personnalisé. Le code suivant montre comment utiliser un type personnalisé comme argument de type pour un <xref:System.Windows.Navigation.PageFunction%601>.

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

Les arguments de type pour le <xref:System.Windows.Navigation.PageFunction%601> fournissent la base de la communication entre une page appelante et la page appelée, qui sont décrites dans les sections suivantes.

Comme vous le verrez, le type identifié avec la déclaration d’un <xref:System.Windows.Navigation.PageFunction%601> joue un rôle important dans le retour des données d’un <xref:System.Windows.Navigation.PageFunction%601> à la page appelante.

### <a name="calling-a-pagefunction-and-passing-parameters"></a>Appel de PageFunction et passage de paramètres

Pour appeler une page, la page appelante doit instancier la page appelée et y accéder à l’aide de la méthode <xref:System.Windows.Navigation.NavigationService.Navigate%2A>. Cela permet à la page appelante de passer les données initiales à la page appelée, par exemple les valeurs par défaut des données recueillies par la page appelée.

Le code suivant montre la page appelée avec un constructeur sans paramètre pour accepter les paramètres de la page appelante.

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

Le code suivant montre la page appelante qui gère l’événement <xref:System.Windows.Documents.Hyperlink.Click> de l' <xref:System.Windows.Documents.Hyperlink> pour instancier la page appelée et lui passer une valeur de chaîne initiale.

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

Vous n’êtes pas obligé de passer des paramètres à la page appelée. Au lieu de cela, vous pouvez procéder comme suit :

- À partir de la page appelante :

  1. Instanciez la <xref:System.Windows.Navigation.PageFunction%601> appelée à l’aide du constructeur sans paramètre.

  2. Stockez les paramètres dans <xref:System.Windows.Application.Properties%2A>.

  3. Accédez à la <xref:System.Windows.Navigation.PageFunction%601> appelée.

- À partir de la <xref:System.Windows.Navigation.PageFunction%601> appelée :

  - Récupérez et utilisez les paramètres stockés dans <xref:System.Windows.Application.Properties%2A>.

Toutefois, comme vous le verrez bientôt, vous devrez quand même utiliser du code pour instancier et accéder à la page appelée afin de recueillir les données qu’elle a retournées. Pour cette raison, le <xref:System.Windows.Navigation.PageFunction%601> doit être maintenu actif ; dans le cas contraire, la prochaine fois que vous accédez à la <xref:System.Windows.Navigation.PageFunction%601>, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] instancie le <xref:System.Windows.Navigation.PageFunction%601> à l’aide du constructeur sans paramètre.

Avant que la page appelée puisse retourner, toutefois, elle doit retourner des données qui peuvent être récupérées par la page appelante.

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Retour de résultat de tâche et de données de tâche à une page appelante

Une fois que l’utilisateur a fini d’utiliser la page appelée, ce qui est indiqué dans cet exemple par un appui sur le bouton Annuler ou OK, la page appelée doit retourner. Étant donné que la page appelante a utilisé la page appelée pour recueillir des données auprès de l’utilisateur, la page appelante nécessite deux types d’informations :

1. Si l’utilisateur a annulé la page appelée (en appuyant sur le bouton OK ou Annuler dans cet exemple). Cela permet à la page appelante de déterminer s’il faut traiter les données recueillies auprès de l’utilisateur par la page appelée.

2. Les données qui ont été fournies par l’utilisateur.

Pour retourner des informations, <xref:System.Windows.Navigation.PageFunction%601> implémente la méthode <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>. L’exemple de code suivant montre comment l’appeler.

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

Dans cet exemple, si l’utilisateur appuie sur le bouton Annuler, une valeur `null` est retournée à la page appelante. Si en revanche il appuie sur le bouton OK, la valeur de chaîne fournie par l’utilisateur est retournée. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est une méthode `protected virtual` que vous appelez pour retourner vos données à la page appelante. Vos données doivent être empaquetées dans une instance du type de <xref:System.Windows.Navigation.ReturnEventArgs%601> générique, dont l’argument de type spécifie le type de valeur retourné par <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A>. De cette façon, lorsque vous déclarez une <xref:System.Windows.Navigation.PageFunction%601> avec un argument de type particulier, vous indiquez qu’un <xref:System.Windows.Navigation.PageFunction%601> retournera une instance du type spécifié par l’argument de type. Dans cet exemple, l’argument de type et, par conséquent, la valeur de retour est de type <xref:System.String>.

Lorsque <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est appelé, la page appelante a besoin d’un moyen de recevoir la valeur de retour du <xref:System.Windows.Navigation.PageFunction%601>. Pour cette raison, <xref:System.Windows.Navigation.PageFunction%601> implémente l’événement <xref:System.Windows.Navigation.PageFunction%601.Return> pour l’appel des pages à gérer. Lorsque <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est appelée, <xref:System.Windows.Navigation.PageFunction%601.Return> est déclenchée, de sorte que la page appelante peut s’inscrire auprès de <xref:System.Windows.Navigation.PageFunction%601.Return> pour recevoir la notification.

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>Suppression de pages de tâche quand une tâche se termine

Quand une page appelée est retournée, et que l’utilisateur ne l’a pas annulée, la page appelante traite les données fournies par l’utilisateur et retournées par la page appelée. L’acquisition de données de cette manière est généralement une opération isolée. Quand la page appelée est retournée, la page appelante doit créer et naviguer vers une nouvelle page appelante pour capturer davantage de données.

Toutefois, sauf si une page appelée est supprimée du journal, un utilisateur pourra revenir à une instance précédente de la page appelante. Le fait qu’un <xref:System.Windows.Navigation.PageFunction%601> soit conservé dans le journal est déterminé par la propriété <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A>. Par défaut, une fonction de page est automatiquement supprimée lorsque <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> est appelé, car <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> a la valeur `true`. Pour conserver une fonction de page dans l’historique de navigation après l’appel de <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, définissez <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> sur `false`.

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>Autres types de navigation structurée

Cette rubrique illustre l’utilisation la plus simple d’un <xref:System.Windows.Navigation.PageFunction%601> pour prendre en charge la navigation structurée appel/retour. Cette base vous permet de créer des types de navigation structurée plus complexes.

Par exemple, parfois plusieurs pages sont requises par une page appelante pour recueillir suffisamment de données auprès d’un utilisateur ou pour effectuer une tâche. En cas d’utilisation de plusieurs pages, on emploie le terme « Assistant ».

Dans d’autres cas, les applications peuvent avoir des topologies de navigation complexes qui dépendent de la navigation structurée pour fonctionner efficacement. Pour plus d’informations, consultez [Vue d’ensemble des topologies de navigation](navigation-topologies-overview.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Vue d’ensemble des topologies de navigation](navigation-topologies-overview.md)
