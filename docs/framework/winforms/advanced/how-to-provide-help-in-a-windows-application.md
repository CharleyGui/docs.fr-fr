---
title: Guide pratique pour fournir de l'aide dans une application Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 405de333ce936a864047e827e60f56a930059e26
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143604"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Guide pratique pour fournir de l'aide dans une application Windows

Vous pouvez utiliser le <xref:System.Windows.Forms.HelpProvider> composant pour joindre des rubriques d’aide dans un fichier d’aide à des contrôles spécifiques sur Windows Forms. Le fichier d’aide peut être au format HTML, ou HTMLHelp 1.x ou ultérieur.

## <a name="provide-help"></a>Fournir de l’aide

1. Dans Visual Studio, dans la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.HelpProvider> composant vers votre formulaire.

     Le composant sera placé dans la barre d’état en bas du Concepteur Windows Forms.

2. Dans la fenêtre **Propriétés** , définissez la <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> propriété sur le fichier d’aide. chm,. col ou. htm.

3. Sélectionnez un autre contrôle sur votre formulaire, puis, dans la fenêtre **Propriétés** , définissez la <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> propriété.

     Il s’agit de la chaîne transmise à <xref:System.Windows.Forms.HelpProvider> votre fichier d’aide par le composant pour appeler la rubrique d’aide appropriée.

4. Dans la fenêtre **Propriétés** , affectez <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> à la propriété une valeur de l' <xref:System.Windows.Forms.HelpNavigator> énumération.

     Ceci détermine la façon dont la propriété **HelpKeyword** est passée au système d’aide. Le tableau suivant montre les paramètres possibles et leur description.

    |Member Name|Description|
    |-----------------|-----------------|
    |AssociateIndex|Spécifie que l’index d’une rubrique spécifiée est exécuté dans l’URL spécifiée.|
    |Rechercher|Spécifie que la page de recherche d’une URL spécifiée est affichée.|
    |Index|Spécifie que l’index d’une URL spécifiée est affiché.|
    |KeywordIndex|Spécifie un mot clé à rechercher et l’action à effectuer dans l’URL spécifiée.|
    |TableOfContents|Spécifie que la table des matières du fichier d’aide HTML 1.0 est affiché.|
    |Rubrique|Spécifie que la rubrique référencée par l’URL spécifiée est affichée.|

 Au moment de l’exécution, en appuyant sur F1 quand le contrôle, pour lequel vous avez défini les propriétés **HelpKeyword** et **HelpNavigator** , a le focus, le fichier d’aide que vous avez associé à ce composant s’ouvre <xref:System.Windows.Forms.HelpProvider> .

 Actuellement, la propriété **HelpNamespace** prend en charge les fichiers d’aide dans les trois formats suivants : HTMLHelp 1.x, HTMLHelp 2.0 et HTML. Par conséquent, vous pouvez définir la propriété **HelpNamespace** sur une `http://` adresse, telle qu’une page Web. Dans ce cas, elle ouvre le navigateur par défaut à la page web avec la chaîne spécifiée dans la propriété **HelpKeyword** utilisée comme ancre. L’ancre est utilisée pour accéder à une partie spécifique d’une page HTML.

> [!IMPORTANT]
> Prenez soin de vérifier toutes les informations envoyées par un client avant de les utiliser dans votre application. Des utilisateurs malveillants peuvent tenter d’envoyer ou d’injecter un script exécutable, des instructions SQL ou un autre code. Avant d’afficher une entrée utilisateur, de la stocker dans une base de données ou de l’utiliser, vérifiez qu’elle ne contient pas d’informations potentiellement dangereuses. Une façon habituelle de le vérifier est d’utiliser une expression régulière pour rechercher des mots clés comme « SCRIPT » quand vous recevez une entrée d’un utilisateur.

Vous pouvez également utiliser le <xref:System.Windows.Forms.HelpProvider> composant pour afficher l’aide contextuelle, même si vous l’avez configuré pour afficher les fichiers d’aide des contrôles de votre Windows Forms. Pour plus d’informations, consultez [Guide pratique pour afficher l’aide contextuelle](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour afficher l’aide contextuelle](how-to-display-pop-up-help.md)
- [Affichage sous forme d’info-bulles de l’aide relative aux contrôles](control-help-using-tooltips.md)
- [Intégration de l’aide d’utilisateur dans les Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
