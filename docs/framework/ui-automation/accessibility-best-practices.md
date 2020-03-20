---
title: Meilleures pratiques d'accessibilité
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: c6f0f31260ffae43e59703ef53dd7ef30a73320b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180295"
---
# <a name="accessibility-best-practices"></a>Meilleures pratiques d'accessibilité
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 La mise en œuvre des pratiques exemplaires suivantes en matière de contrôles ou d’applications améliorera leur accessibilité pour les personnes qui utilisent des appareils de technologie d’assistance. Une grande partie de ces meilleures pratiques se concentrent sur une bonne conception de l' [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] . Chaque meilleure pratique inclut des informations d'implémentation des contrôles ou applications [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] . Dans de nombreux cas, le travail nécessaire pour appliquer ces meilleures pratiques est déjà inclus dans les contrôles [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] .  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Accès par programme  
 L'accès par programmation implique de vérifier que tous les éléments de l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sont étiquetés, que les valeurs des propriétés sont exposées et que les événements appropriés sont déclenchés. Pour les contrôles [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] standard, l'essentiel de ce travail est déjà effectué via <xref:System.Windows.Automation.Peers.AutomationPeer>. Les contrôles personnalisés nécessitent un travail supplémentaire pour vérifier que l'accès par programmation est correctement implémenté.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Activer l'accès par programmation à tous les éléments de l'interface utilisateur et le texte  
 Les éléments de l’interface utilisateur (interface utilisateur) doivent permettre un accès programmatique. Si l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] est un contrôle [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] standard, la prise en charge de l'accès par programmation est incluse dans le contrôle. Si le contrôle est un contrôle personnalisé, tel qu'un contrôle qui a été sous-classé à partir d'un contrôle commun ou un contrôle qui a été sous-classé à partir de Control, vous devez alors vérifier l'implémentation d' <xref:System.Windows.Automation.Peers.AutomationPeer> pour les zones qui peuvent nécessiter des modifications.  
  
 Suite à cette pratique exemplaire permet aux fournisseurs de technologie [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]d’assistance d’identifier et de manipuler des éléments de votre produit .  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Placer des noms, titres et descriptions sur les objets, les cadres et les pages de l'interface utilisateur  
 Les technologies d'assistance, particulièrement les lecteurs d'écran, utilisent le titre pour déterminer l'emplacement du cadre, de l'objet ou de la page dans le schéma de navigation. Par conséquent, le titre doit être très descriptif. Par exemple, un titre de page web tel que « Page web Microsoft » n'est d'aucune utilité si l'utilisateur a navigué de façon poussée dans une zone particulière. Un titre descriptif est une information critique pour les utilisateurs malvoyants ou non-voyants qui dépendent des lecteurs d'écran. De même, pour [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] les contrôles, <xref:System.Windows.Automation.AutomationProperties.NameProperty> et <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> sont importants pour les dispositifs de technologie d’assistance.  
  
 La suite de cette pratique exemplaire permet [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] aux technologies d’assistance d’identifier et de manipuler dans les commandes et les applications des échantillons.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Vérifier que les événements par programmation sont déclenchés par toutes les activités de l'interface utilisateur  
 La suite de cette pratique exemplaire permet aux [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] technologies d’assistance d’écouter les changements dans le et d’aviser l’utilisateur de ces changements.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>Paramètres utilisateur  
 La meilleure pratique décrite dans cette section permet de vérifier que les contrôles et les applications n'écrasent pas les paramètres utilisateur.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Respecter tous les paramètres au niveau du système et ne pas interférer avec les fonctions d'accessibilité  
 Les utilisateurs peuvent utiliser le Panneau de configuration pour définir certains indicateurs au niveau du système ; d'autres indicateurs peuvent être définis par programmation. Ces paramètres ne doivent pas être modifiés par des contrôles ou des applications. Les applications doivent aussi prendre en charge les paramètres d'accessibilité du système d'exploitation hôte.  
  
 L'application de cette meilleure pratique permet aux utilisateurs de définir des paramètres d'accessibilité et de savoir que ceux-ci ne seront pas modifiés par les applications.  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>Conception de l'interface utilisateur visuelle  
 Les meilleures pratiques de cette section garantissent que les contrôles ou les applications utilisent efficacement la couleur et les images et peuvent être utilisées par les technologies d’assistance.  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>Ne pas coder en dur les couleurs  
 Les personnes qui ne perçoivent pas les couleurs, qui ont une acuité visuelle réduite ou qui utilisent un écran noir et blanc risquent de ne pas pouvoir utiliser les applications dont les couleurs sont codées en dur.  
  
 L'application de cette meilleure pratique permet aux utilisateurs d'ajuster les combinaisons de couleurs en fonction de leurs besoins.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Prendre en charge le contraste élevé et tous les attributs de l'affichage du système  
 Les applications ne doivent pas perturber ou désactiver les paramètres sélectionnés par l'utilisateur et définis au niveau du système, ni les sélections des couleurs ou d'autres paramètres et attributs au niveau du système. Les paramètres au niveau du système qui sont adoptés par un utilisateur améliorent l'accessibilité des applications, ils ne doivent donc pas être désactivés ou ignorés par les applications. Les couleurs doivent être utilisées dans leur combinaison correcte du premier plan sur l'arrière-plan afin de fournir un contraste approprié. Les couleurs qui ne se marient pas bien ne doivent pas être mélangées, et les couleurs ne doivent pas être inversées.  
  
 De nombreux utilisateurs requièrent des combinaisons de contraste élevé spécifiques, telles que du texte blanc sur un arrière-plan noir. Les afficher de façon inversée, comme du texte noir sur un arrière-plan blanc, provoque la bavure de l'arrière-plan sur le premier plan et peut entraîner des difficultés de lecture pour certains utilisateurs.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Vérifier que toute l'interface utilisateur est correctement mise à l'échelle par tous les paramètres PPP  
 Assurez-vous [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] que tous peuvent correctement échelle par n’importe quel point par pouce (dpi) réglage. En outre, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] assurez-vous que les éléments s’adaptent dans un écran de 1024 x 768 avec 120 points par pouce (dpi).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navigation  
 Les meilleures pratiques décrites dans cette section permettent de vérifier que la navigation est traitée pour les contrôles et les applications.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Fournir une interface de clavier pour tous les éléments de l'interface utilisateur  
 Les taquets de tabulation, notamment lorsqu'ils sont bien prévus, offrent aux utilisateurs une autre possibilité de naviguer dans l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Les applications doivent fournir les interfaces de clavier suivantes :  
  
- des taquets de tabulations pour tous les contrôles avec lesquels l'utilisateur peut interagir, comme les boutons, les liens ou les zones de liste ;  
  
- un ordre logique de tabulation.  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>Afficher le focus clavier  
 Les utilisateurs ont besoin de savoir quel est l'objet qui a le focus clavier afin de pouvoir anticiper l'effet de leurs séquences de touches. Pour mettre en surbrillance le focus clavier, utilisez des couleurs, des fontes ou des graphiques tels que les rectangles ou l'agrandissement. Pour mettre en évidence de façon audible le focus clavier, modifiez le volume, la fréquence du son ou la qualité de la tonalité.  
  
 Pour éviter toute confusion, les applications doivent cacher tous les indicateurs de focus visuels et estomper les sélections situées sur les fenêtres ou les panneaux inactifs.  
  
 Les applications doivent procéder comme suit en ce qui concerne le focus clavier :  
  
- un des éléments doit toujours avoir le focus clavier ;  
  
- le focus clavier doit être visible et évident ;  
  
- les sélections et/ou les éléments possédant le focus doivent être visuellement mis en surbrillance.  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Prendre en charge les standards de navigation et les schémas de navigation puissants  
 Des aspects différents de la navigation au clavier fournissent aux utilisateurs des moyens différents pour naviguer dans l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Les applications doivent fournir les interfaces de clavier suivantes :  
  
- touches de raccourci et touches d'accès rapide soulignées pour toutes les commandes, ainsi que pour tous les menus et contrôles ;  
  
- raccourcis clavier vers les liens importants ;  
  
- tous les éléments de menu ont une touche d'accès rapide ; tous les boutons ont des touches accélérateur ; toutes les commandes ont une touche accélérateur.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Ne pas laisser l'emplacement de la souris interférer avec la navigation au clavier  
 L'emplacement de la souris ne doit pas interférer avec la navigation au clavier. Par exemple, si la souris est positionnée quelque part et que l'utilisateur est en train de naviguer avec le clavier, il ne doit pas se produire de clic de souris, à moins qu'il soit initié par l'utilisateur.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Interface multimodale  
 Les meilleures pratiques décrites dans cette section vérifient que l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] de l'application inclut des alternatives aux éléments visuels.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Fournir des équivalents sélectionnables par l'utilisateur pour les éléments non-texte  
 Pour chaque élément non-texte, fournissez un équivalent sélectionnable par l'utilisateur pour le texte, les transcriptions ou les descriptions audio, comme du texte alternatif, des légendes ou une rétroaction visuelle.  
  
 Les éléments non-texte couvrent une large gamme d'éléments de l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , notamment : les images, les régions d'images interactives, les animations, les applets, les cadres, les scripts, les boutons graphiques, les sons, les fichiers audio autonomes et la vidéo. Les éléments non-texte sont importants lorsqu'ils contiennent des informations visuelles, de la parole ou des informations audio générales auxquelles l'utilisateur a besoin d'accéder pour comprendre le contenu de l' [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Utiliser la couleur mais fournir également des alternatives à la couleur  
 Utilisez la couleur pour améliorer, accentuer ou réitérer des informations déjà affichées par d'autres moyens, mais ne communiquez pas des informations uniquement à l'aide des couleurs. Les utilisateurs qui ne perçoivent pas les couleurs ou qui ont un écran monochrome ont besoin d'alternatives à la couleur.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Utiliser les API d'entrée standard avec des appels indépendants de l’appareil  
 Les appels indépendants de l’appareil garantissent l’égalité des [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]fonctions clavier et souris, tout en fournissant une technologie d’assistance avec les informations nécessaires sur le .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.Peers>
- [Contrôle personnalisé NumericUpDown avec thème et prise en charge d'UI Automation, exemple](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Recommandations en matière de conception d’interface utilisateur clavier](https://docs.microsoft.com/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
