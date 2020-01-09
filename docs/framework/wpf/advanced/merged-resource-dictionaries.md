---
title: Dictionnaires de ressources fusionnés
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 899955a9f3302e67de4efa0ce0cb6baf6bf0ec5d
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559779"
---
# <a name="merged-resource-dictionaries"></a>Dictionnaires de ressources fusionnés
Les ressources [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prennent en charge une fonctionnalité de dictionnaire de ressources fusionné. Cette fonctionnalité offre un moyen de définir la partie ressources d’une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] en dehors de l’application [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compilée. Les ressources peuvent ensuite être partagées entre les applications et sont aussi isolées plus facilement pour la localisation.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Introduction d’un dictionnaire de ressources fusionné  
 Dans le balisage, la syntaxe suivante permet d’introduire un dictionnaire de ressources fusionné dans une page :  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Notez que l’élément <xref:System.Windows.ResourceDictionary> n’a pas de [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md), qui est généralement requise pour tous les éléments d’une collection de ressources. Toutefois, une autre <xref:System.Windows.ResourceDictionary> référence dans la collection de <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> est un cas spécial, réservé à ce scénario de dictionnaire de ressources fusionné. La <xref:System.Windows.ResourceDictionary> qui introduit un dictionnaire de ressources fusionné ne peut pas avoir de [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md). En règle générale, chaque <xref:System.Windows.ResourceDictionary> dans la collection de <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> spécifie un attribut <xref:System.Windows.ResourceDictionary.Source%2A>. La valeur de <xref:System.Windows.ResourceDictionary.Source%2A> doit être un URI (Uniform Resource Identifier) qui correspond à l’emplacement du fichier de ressources à fusionner. La destination de cet URI doit être un autre fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], avec <xref:System.Windows.ResourceDictionary> comme élément racine.  
  
> [!NOTE]
> Il est légal de définir des ressources au sein d’un <xref:System.Windows.ResourceDictionary> qui est spécifié comme dictionnaire fusionné, soit comme alternative à spécifier <xref:System.Windows.ResourceDictionary.Source%2A>, soit en plus des ressources incluses dans la source spécifiée. Cependant, il ne s’agit pas d’un scénario courant ; le scénario principal pour les dictionnaires fusionnés consiste à fusionner des ressources à partir d’emplacements de fichiers externes. Si vous souhaitez spécifier des ressources dans le balisage d’une page, vous devez généralement les définir dans le <xref:System.Windows.ResourceDictionary> principal et non dans les dictionnaires fusionnés.  
  
## <a name="merged-dictionary-behavior"></a>Comportement d’un dictionnaire fusionné  
 Les ressources d’un dictionnaire fusionné occupent un emplacement dans la portée de recherche des ressources, qui se trouve juste après la portée du dictionnaire de ressources principal dans lequel elles sont fusionnées. Même si un dictionnaire individuel ne doit contenir qu’une seule clé de ressource, un ensemble de dictionnaires fusionnés peut contenir plusieurs fois la même clé. Dans ce cas, la ressource retournée provient du dernier dictionnaire trouvé de manière séquentielle dans la collection <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Si la collection <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> a été définie dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], l’ordre des dictionnaires fusionnés dans la collection correspond à l’ordre des éléments comme indiqué dans le balisage. Si une clé est définie à la fois dans le dictionnaire principal et dans un dictionnaire fusionné, la ressource retournée provient du dictionnaire principal. Ces règles de portée s’appliquent de la même façon aux références de ressources statiques et aux références de ressources dynamiques.  
  
### <a name="merged-dictionaries-and-code"></a>Dictionnaires fusionnés et code  
 Il est possible d’ajouter des dictionnaires fusionnés à un dictionnaire `Resources` avec du code. La valeur par défaut, initialement vide <xref:System.Windows.ResourceDictionary> qui existe pour toute propriété `Resources` possède également une propriété de collection par défaut, initialement vide <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Pour ajouter un dictionnaire fusionné par le biais du code, vous obtenez une référence au <xref:System.Windows.ResourceDictionary>principal souhaité, obtenez sa valeur de propriété <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> et appelez `Add` sur le `Collection` générique contenu dans <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. L’objet que vous ajoutez doit être un nouveau <xref:System.Windows.ResourceDictionary>. Dans le code, vous ne définissez pas la propriété <xref:System.Windows.ResourceDictionary.Source%2A>. Au lieu de cela, vous devez obtenir un objet <xref:System.Windows.ResourceDictionary> en en créant un ou en chargeant un objet. L’une des façons de charger un <xref:System.Windows.ResourceDictionary> existant pour appeler <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> sur un flux de fichier de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] existant qui a une racine de <xref:System.Windows.ResourceDictionary>, puis de convertir la valeur de retour <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> en <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>URI de dictionnaire de ressources fusionné  
 Il existe plusieurs techniques pour inclure un dictionnaire de ressources fusionné, qui sont indiquées par le format d’URI (Uniform Resource Identifier) que vous allez utiliser. Pour simplifier, ces techniques peuvent être divisées en deux catégories : les ressources qui sont compilés dans le cadre du projet et celles qui ne le sont pas.  
  
 Pour les ressources qui sont compilés dans le cadre du projet, vous pouvez utiliser un chemin relatif qui fait référence à l’emplacement de la ressource. Le chemin relatif est évalué pendant la compilation. Votre ressource doit être définie dans le cadre du projet comme une action de génération de ressources. Si vous incluez un fichier de ressources .xaml dans le projet en tant que ressource, vous n’avez pas besoin de copier le fichier de ressources dans le répertoire de sortie, car la ressource est déjà incluse dans l’application compilée. Vous pouvez aussi utiliser l’action de génération de contenu, mais vous devez dans ce cas copier les fichiers dans le répertoire de sortie et déployer aussi les fichiers de ressources de ce répertoire vers le fichier exécutable.  
  
> [!NOTE]
> N’utilisez pas l’action de génération de ressource incorporée. L’action de génération elle-même est prise en charge pour les applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mais la résolution de <xref:System.Windows.ResourceDictionary.Source%2A> n’incorpore pas <xref:System.Resources.ResourceManager>et ne peut donc pas séparer la ressource individuelle du flux. Vous pouvez toujours utiliser la ressource incorporée à d’autres fins tant que vous avez également utilisé <xref:System.Resources.ResourceManager> pour accéder aux ressources.  
  
 Une technique similaire consiste à utiliser un URI à en-tête pack dans un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et y faire référence en tant que source. Un URI à en-tête pack active les références aux composants des assemblys référencés et d’autres techniques. Pour plus d’informations sur les URI à en-tête pack, consultez [Fichiers de ressources, de contenu et de données d’une application WPF](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 Pour les ressources qui ne sont pas compilées dans le cadre du projet, l’URI est évalué au moment de l’exécution. Vous pouvez utiliser un transport d’URI courant, tel que file: ou http:, pour faire référence au fichier de ressources. L’inconvénient d’une utilisation de l’approche de ressource non compilée est que l’accès file: nécessite des étapes de déploiement supplémentaires, et l’accès http: implique la zone de sécurité Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Réutilisation des dictionnaires fusionnés  
 Vous pouvez réutiliser ou partager les dictionnaires de ressources fusionnés entre les applications, car le dictionnaire de ressources à fusionner peut être référencé via n’importe quel URI (Uniform Resource Identifier) valide. La procédure exacte à suivre dans ce cas dépend de votre stratégie de déploiement d’application et du modèle d’application suivi. La stratégie d’URI à en-tête pack mentionnée plus haut offre un moyen de se procurer communément une ressource fusionnée parmi plusieurs projets pendant le développement en partageant une référence d’assembly. Dans ce scénario, les ressources sont toujours distribuées par le client, et au moins l’une des applications doit déployer l’assembly référencé. Il est aussi possible de référencer des ressources fusionnées via un URI distribué qui utilise le protocole http.  
  
 L’écriture de dictionnaires fusionnés en tant que fichiers d’application locaux ou dans un espace de stockage partagé local est un autre scénario possible de déploiement de dictionnaires fusionnés ou d’applications.  
  
### <a name="localization"></a>Localisation  
 Si les ressources à localiser sont isolées dans des dictionnaires qui sont fusionnés dans des dictionnaires principaux et conservées dans un format [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] libre, ces fichiers peuvent être localisés séparément. Cette technique est une solution de rechange simplifiée de la localisation des assemblys de ressources satellites. Pour plus d’informations, consultez [Vue d’ensemble de la globalisation et de la localisation WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.ResourceDictionary>
- [Ressources XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Ressources et code](resources-and-code.md)
- [Fichiers de ressources, de contenu et de données d’une application WPF](../app-development/wpf-application-resource-content-and-data-files.md)
