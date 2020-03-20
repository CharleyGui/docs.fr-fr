---
title: Attributs et commentaires de localisation
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 7281ca6d76f0d2ffb5020feba236b4e4cf948bdd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141586"
---
# <a name="localization-attributes-and-comments"></a>Attributs et commentaires de localisation
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]les commentaires de localisation sont des propriétés, à l’intérieur du code source XAML, fournis par les développeurs pour fournir des règles et des conseils pour la localisation. Les commentaires de localisation [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contiennent deux ensembles d’informations : les attributs d’adaptabilité et les commentaires de localisation au format libre. Les attributs d’adaptabilité sont utilisés par l’API de localisation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour indiquer les ressources à localiser. Les commentaires au format libre sont des informations que l’auteur de l’application veut inclure.  

<a name="Localizer_Comments_"></a>
## <a name="localization-comments"></a>Commentaires de localisation  
 Si les auteurs d’applications de balisage ont des exigences pour des éléments spécifiques dans XAML, tels que des contraintes sur la longueur du texte, la famille de police, ou la taille de police, ils peuvent transmettre ces informations aux localisateurs avec des commentaires dans le code XAML. Le processus permettant d’ajouter des commentaires au code source est le suivant :  
  
1. Le développeur d’applications ajoute des commentaires de localisation au code source XAML.  
  
2. Pendant le processus de génération, vous pouvez indiquer dans le fichier .proj si vous voulez laisser les commentaires de localisation au format libre dans l’assembly et retirer tout ou partie des commentaires. Les commentaires supprimés sont placés dans un fichier distinct. Pour spécifier votre choix, utilisez une balise `LocalizationDirectivesToLocFile`, par exemple :  
  
     `<LocalizationDirectivesToLocFile>`*valeur*`</LocalizationDirectivesToLocFile>`  
  
3. Les valeurs qui peuvent être attribuées sont :  
  
    - **None** : les commentaires et les attributs sont conservés dans l’assembly et aucun fichier distinct n’est généré.  
  
    - **CommentsOnly** : seuls les commentaires sont retirés de l’assembly et placés dans un fichier LocFile distinct.  
  
    - **All** : les commentaires et les attributs sont retirés de l’assembly et placés dans un fichier LocFile distinct.  
  
4. Lorsque des ressources localisables sont extraites de BAML, les attributs de localisation sont respectés par l’API de localisation BAML.  
  
5. Les fichiers de commentaires de localisation, qui contiennent uniquement des commentaires au format libre, sont incorporés ultérieurement au processus de localisation.  
  
 L’exemple suivant montre comment ajouter des commentaires de localisation à un fichier XAML.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 Dans l’exemple précédent, la section Localization.Attributes contient les attributs de localisation et la section Localization.Comments les commentaires au format libre. Les tableaux ci-dessous présentent les différents attributs et commentaires destinés au localisateur, ainsi que leur signification.  
  
|Attributs de localisation|Signification|  
|-----------------------------|-------------|  
|$Content (Unmodifiable Readable Text)|Le contenu de l’élément TextBlock ne peut pas être modifié. Les localisateurs ne peuvent pas changer le mot « Microsoft ». Le contenu est visible (Readable) pour le localisateur. Le contenu appartient à la catégorie texte.|  
|FontFamily (Unmodifiable Readable)|La propriété de famille de polices de l’élément TextBlock ne peut pas être changée, mais elle est visible pour le localisateur.|  
  
|Commentaires de localisation au format libre|Signification|  
|--------------------------------------|-------------|  
|$Content (Trademark)|L’auteur de l’application informe le localisateur que le contenu de l’élément TextBlock est une marque.|  
|FontSize (Trademark font size)|L’auteur de l’application indique que la propriété de taille de police doit être conforme à la taille standard de la marque.|  
  
### <a name="localizability-attributes"></a>Attributs d’adaptabilité  
 Les informations présentes dans la section Localization.Attributes contiennent une liste de paires : le nom de la valeur ciblée et les valeurs d’adaptabilité associées. Le nom cible peut être un nom de propriété ou le nom $Content spécial. S’il s’agit d’un nom de propriété, la valeur ciblée est la valeur de la propriété. S’il s’agit du nom $Content, la valeur ciblée est le contenu de l’élément.  
  
 Il existe trois types d'attributs :  
  
- **Catégorie**. spécifie si une valeur doit pouvoir être modifiée à partir d’un outil de localisation. Consultez <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Lisibilité**. spécifie si un outil de localisation doit lire (et afficher) une valeur. Consultez <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Modifiability**. spécifie si un outil de localisation autorise la modification d’une valeur. Consultez <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Ces attributs peuvent être spécifiés dans n’importe quel ordre et doivent être séparés par un espace. Si des attributs dupliqués sont spécifiés, le dernier attribut remplace les précédents. Par exemple, Localization.Attributes = "Unmodifiable Modifiable" indique que la valeur est Modifiable, car c’est le dernier attribut indiqué.  
  
 La signification des attributs Modifiabilité et Lisibilité est évidente. L’attribut Catégorie comprend des catégories prédéfinies qui aident le localisateur à traduire le texte. Certaines catégories, telles que Text, Label et Title, renseignent le localisateur sur la façon de traduire le texte. Il existe aussi des catégories spéciales : None, Inherit, Ignore et NeverLocalize.  
  
 Le tableau suivant indique la signification de ces catégories spéciales.  
  
|Category|Signification|  
|--------------|-------------|  
|None|La valeur ciblée n’a pas de catégorie définie.|  
|Hériter|La valeur ciblée hérite de la catégorie de son parent.|  
|Ignorer|La valeur ciblée est ignorée dans le processus de localisation. Cette catégorie affecte uniquement la valeur actuelle. Elle n’affecte pas les nœuds enfants.|  
|NeverLocalize|La valeur actuelle ne peut pas être localisée. Cette catégorie est héritée par les enfants d’un élément.|  
  
<a name="Localization_Comments"></a>
## <a name="localization-comments"></a>Commentaires de localisation  
 La section Localization.Comments contient des chaînes ouvertes relatives à la valeur ciblée. Les développeurs d’applications peuvent ajouter des informations pour donner des conseils aux localisateurs sur la façon de traduire le texte des applications. Le format des commentaires peut être n’importe quelle chaîne délimitée par des « () ». Utilisez « \\ » pour spécifier des caractères d’échappement.  
  
## <a name="see-also"></a>Voir aussi

- [Globalisation pour WPF](globalization-for-wpf.md)
- [Utiliser la disposition automatique pour créer un bouton](how-to-use-automatic-layout-to-create-a-button.md)
- [Utiliser une grille pour la disposition automatique](how-to-use-a-grid-for-automatic-layout.md)
- [Localiser une application](how-to-localize-an-application.md)
