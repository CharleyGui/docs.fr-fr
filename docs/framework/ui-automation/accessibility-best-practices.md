---
title: Meilleures pratiques d'accessibilité
description: En savoir plus sur les meilleures pratiques d’accessibilité dans .NET. Explorez l’accès par programmation, les paramètres utilisateur, la conception de l’interface utilisateur visuelle, la navigation et les interfaces multimodales.
ms.date: 03/30/2017
helpviewer_keywords:
- best practices for accessibility
- accessibility, best practices for
ms.assetid: e6d5cd98-21a3-4b01-999c-fb953556d0e6
ms.openlocfilehash: 1c01cfe8fdfb285ee5cbc586cc0c549365ef72ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543145"
---
# <a name="accessibility-best-practices"></a>Meilleures pratiques d’accessibilité

> [!NOTE]
> Cet article s’adresse aux développeurs .NET Framework qui souhaitent utiliser les classes UI Automation gérées définies dans l' <xref:System.Windows.Automation> espace de noms. Pour obtenir les informations les plus récentes sur UI Automation, consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 L’implémentation des meilleures pratiques suivantes dans les contrôles ou les applications améliore leur accessibilité pour les personnes qui utilisent des appareils de technologie d’assistance. La plupart de ces meilleures pratiques se concentrent sur la bonne conception de l’interface utilisateur. Chaque meilleure pratique comprend des informations d’implémentation pour les contrôles ou les applications Windows Presentation Foundation (WPF). Dans de nombreux cas, le travail pour répondre à ces meilleures pratiques est déjà inclus dans les contrôles WPF.  
  
<a name="Programmatic_Access"></a>
## <a name="programmatic-access"></a>Accès par programme  
 L’accès par programmation implique de s’assurer que tous les éléments d’interface utilisateur sont étiquetés, que les valeurs des propriétés sont exposées et que les événements appropriés sont déclenchés. Pour les contrôles WPF standard, la majeure partie de ce travail est déjà effectuée par le biais de <xref:System.Windows.Automation.Peers.AutomationPeer> . Les contrôles personnalisés nécessitent un travail supplémentaire pour vérifier que l'accès par programmation est correctement implémenté.  
  
<a name="Enable_Programmatic_Access_to_all_UI_Elements_and_Text"></a>
### <a name="enable-programmatic-access-to-all-ui-elements-and-text"></a>Activer l'accès par programmation à tous les éléments de l'interface utilisateur et le texte  
 Les éléments de l’interface utilisateur doivent activer l’accès par programme. Si l’interface utilisateur est un contrôle WPF standard, la prise en charge de l’accès par programmation est incluse dans le contrôle. Si le contrôle est un contrôle personnalisé, tel qu'un contrôle qui a été sous-classé à partir d'un contrôle commun ou un contrôle qui a été sous-classé à partir de Control, vous devez alors vérifier l'implémentation d' <xref:System.Windows.Automation.Peers.AutomationPeer> pour les zones qui peuvent nécessiter des modifications.  
  
 Suivre cette meilleure pratique permet aux fournisseurs de technologies d’assistance d’identifier et de manipuler les éléments de l’interface utilisateur de votre produit.  
  
<a name="Place_Names__Titles_and_Descriptions_on_UI_Objects_"></a>
### <a name="place-names-titles-and-descriptions-on-ui-objects-frames-and-pages"></a>Placer des noms, titres et descriptions sur les objets, les cadres et les pages de l'interface utilisateur  
 Les technologies d'assistance, particulièrement les lecteurs d'écran, utilisent le titre pour déterminer l'emplacement du cadre, de l'objet ou de la page dans le schéma de navigation. Par conséquent, le titre doit être descriptif. Par exemple, un titre de page web tel que « Page web Microsoft » n'est d'aucune utilité si l'utilisateur a navigué de façon poussée dans une zone particulière. Un titre descriptif est une information critique pour les utilisateurs malvoyants ou non-voyants qui dépendent des lecteurs d'écran. De même, pour les contrôles WPF, <xref:System.Windows.Automation.AutomationProperties.NameProperty> et <xref:System.Windows.Automation.AutomationProperties.HelpTextProperty> sont importants pour les appareils de technologie d’assistance.  
  
 Suivre cette meilleure pratique permet aux technologies d’assistance d’identifier et de manipuler l’interface utilisateur dans des exemples de contrôles et d’applications.  
  
<a name="Ensure_Programmatic_Events_are_Triggered_by_all_UI"></a>
### <a name="ensure-programmatic-events-are-triggered-by-all-ui-activities"></a>Vérifier que les événements par programmation sont déclenchés par toutes les activités de l'interface utilisateur  
 Suivre cette meilleure pratique permet aux technologies d’assistance d’écouter les modifications apportées à l’interface utilisateur et d’informer l’utilisateur de ces modifications.  
  
<a name="User_Settings"></a>
## <a name="user-settings"></a>Paramètres utilisateur  
 La meilleure pratique décrite dans cette section permet de vérifier que les contrôles et les applications n'écrasent pas les paramètres utilisateur.  
  
<a name="Respect_all_System_Wide_Settings_and_do_not_Interfere"></a>
### <a name="respect-all-system-wide-settings-and-do-not-interfere-with-accessibility-functions"></a>Respecter tous les paramètres au niveau du système et ne pas interférer avec les fonctions d'accessibilité  
 Les utilisateurs peuvent utiliser le Panneau de configuration pour définir certains indicateurs au niveau du système ; d'autres indicateurs peuvent être définis par programmation. Ces paramètres ne doivent pas être modifiés par des contrôles ou des applications. Les applications doivent aussi prendre en charge les paramètres d'accessibilité du système d'exploitation hôte.  
  
 L'application de cette meilleure pratique permet aux utilisateurs de définir des paramètres d'accessibilité et de savoir que ceux-ci ne seront pas modifiés par les applications.  
  
<a name="Visual_UI_Design"></a>
## <a name="visual-ui-design"></a>Conception de l'interface utilisateur visuelle  
 Les meilleures pratiques décrites dans cette section garantissent que les contrôles ou les applications utilisent la couleur et les images de manière efficace et peuvent être utilisés par les technologies d’assistance.  
  
<a name="Don_t_Hard_Code_Colors"></a>
### <a name="dont-hard-code-colors"></a>Ne pas coder en dur les couleurs  
 Les personnes qui ne perçoivent pas les couleurs, qui ont une acuité visuelle réduite ou qui utilisent un écran noir et blanc risquent de ne pas pouvoir utiliser les applications dont les couleurs sont codées en dur.  
  
 L'application de cette meilleure pratique permet aux utilisateurs d'ajuster les combinaisons de couleurs en fonction de leurs besoins.  
  
<a name="Support_High_Contrast_and_all_System_Display_Attributes"></a>
### <a name="support-high-contrast-and-all-system-display-attributes"></a>Prendre en charge le contraste élevé et tous les attributs de l'affichage du système  
 Les applications ne doivent pas perturber ou désactiver les paramètres sélectionnés par l'utilisateur et définis au niveau du système, ni les sélections des couleurs ou d'autres paramètres et attributs au niveau du système. Les paramètres au niveau du système qui sont adoptés par un utilisateur améliorent l'accessibilité des applications, ils ne doivent donc pas être désactivés ou ignorés par les applications. Les couleurs doivent être utilisées dans leur combinaison correcte du premier plan sur l'arrière-plan afin de fournir un contraste approprié. Ne mélangez pas les couleurs non liées et n’inversez pas les couleurs.  
  
 De nombreux utilisateurs requièrent des combinaisons de contraste élevé spécifiques, telles que du texte blanc sur un arrière-plan noir. Les afficher de façon inversée, comme du texte noir sur un arrière-plan blanc, provoque la bavure de l'arrière-plan sur le premier plan et peut entraîner des difficultés de lecture pour certains utilisateurs.  
  
<a name="Ensure_all_UI_Correctly_Scales_by_any_DPI_Setting"></a>
### <a name="ensure-all-ui-correctly-scales-by-any-dpi-setting"></a>Vérifier que toute l'interface utilisateur est correctement mise à l'échelle par tous les paramètres PPP  
 Assurez-vous que toute l’interface utilisateur peut être mise à l’échelle avec n’importe quel paramètre en points par pouce (dpi). Assurez-vous également que les éléments d’interface utilisateur s’ajustent à un écran de 1024 x 768 avec 120 points par pouce (dpi).  
  
<a name="Navigation"></a>
## <a name="navigation"></a>Navigation  
 Les meilleures pratiques décrites dans cette section permettent de vérifier que la navigation est traitée pour les contrôles et les applications.  
  
<a name="Provide_Keyboard_Interface_for_all_UI_Elements"></a>
### <a name="provide-keyboard-interface-for-all-ui-elements"></a>Fournir une interface de clavier pour tous les éléments de l'interface utilisateur  
 Les taquets de tabulation, en particulier lorsqu’ils sont soigneusement planifiés, offrent aux utilisateurs une autre façon de naviguer dans l’interface utilisateur.  
  
 Les applications doivent fournir les interfaces de clavier suivantes :  
  
- des taquets de tabulations pour tous les contrôles avec lesquels l'utilisateur peut interagir, comme les boutons, les liens ou les zones de liste ;  
  
- un ordre logique de tabulation.  
  
<a name="Show_the_Keyboard_Focus"></a>
### <a name="show-the-keyboard-focus"></a>Afficher le focus clavier  
 Les utilisateurs ont besoin de savoir quel est l'objet qui a le focus clavier afin de pouvoir anticiper l'effet de leurs séquences de touches. Pour mettre en surbrillance le focus clavier, utilisez des couleurs, des fontes ou des graphiques tels que les rectangles ou l'agrandissement. Pour mettre en surbrillance de façon audible le focus clavier, modifiez le volume, le tangage ou la qualité tonale.  
  
 Pour éviter toute confusion, les applications doivent cacher tous les indicateurs de focus visuels et estomper les sélections situées sur les fenêtres ou les panneaux inactifs.  
  
 Les applications doivent procéder comme suit en ce qui concerne le focus clavier :  
  
- un des éléments doit toujours avoir le focus clavier ;  
  
- le focus clavier doit être visible et évident ;  
  
- les sélections et/ou les éléments possédant le focus doivent être visuellement mis en surbrillance.  
  
<a name="Support_Navigation_Standards_and_Powerful_Navigation"></a>
### <a name="support-navigation-standards-and-powerful-navigation-schemes"></a>Prendre en charge les standards de navigation et les schémas de navigation puissants  
 Différents aspects de la navigation au clavier offrent aux utilisateurs différents moyens de naviguer dans l’interface utilisateur.  
  
 Les applications doivent fournir les interfaces de clavier suivantes :  
  
- touches de raccourci et touches d’accès soulignées pour toutes les commandes, tous les menus et tous les contrôles  
  
- raccourcis clavier vers les liens importants ;  
  
- tous les éléments de menu ont une touche d'accès rapide ; tous les boutons ont des touches accélérateur ; toutes les commandes ont une touche accélérateur.  
  
<a name="Do_not_let_Mouse_Location_Interfere_with_Keyboard"></a>
### <a name="do-not-let-mouse-location-interfere-with-keyboard-navigation"></a>Ne pas laisser l'emplacement de la souris interférer avec la navigation au clavier  
 L'emplacement de la souris ne doit pas interférer avec la navigation au clavier. Par exemple, si la souris est positionnée sur un emplacement et que l’utilisateur navigue avec le clavier, un clic de souris ne doit pas se produire, sauf si elle est lancée par l’utilisateur.  
  
<a name="Multimodal_Interface"></a>
## <a name="multimodal-interface"></a>Interface multimodale  
 Les meilleures pratiques décrites dans cette section garantissent que l’interface utilisateur de l’application comprend des alternatives pour les éléments visuels.  
  
<a name="Provide_User_Selectable_Equivalents_for_Non_Text"></a>
### <a name="provide-user-selectable-equivalents-for-non-text-elements"></a>Fournir des équivalents sélectionnables par l'utilisateur pour les éléments non-texte  
 Pour chaque élément non-texte, fournissez un équivalent sélectionnable par l'utilisateur pour le texte, les transcriptions ou les descriptions audio, comme du texte alternatif, des légendes ou une rétroaction visuelle.  
  
 Les éléments non-texte couvrent un large éventail d’éléments d’interface utilisateur, notamment les images, les zones de l’image interactive, les animations, les applets, les cadres, les scripts, les boutons graphiques, les sons, les fichiers audio autonomes et la vidéo. Les éléments non-texte sont importants lorsqu’ils contiennent des informations visuelles, de la parole ou des informations audio générales auxquelles l’utilisateur a besoin d’accéder pour comprendre le contenu de l’interface utilisateur.  
  
<a name="Use_Color_but_also_Provide_Alternatives_to_Color"></a>
### <a name="use-color-but-also-provide-alternatives-to-color"></a>Utiliser la couleur mais fournir également des alternatives à la couleur  
 Utilisez la couleur pour améliorer, accentuer ou réitérer des informations déjà affichées par d'autres moyens, mais ne communiquez pas des informations uniquement à l'aide des couleurs. Les utilisateurs qui ne perçoivent pas les couleurs ou qui ont un écran monochrome ont besoin d'alternatives à la couleur.  
  
<a name="Use_Standard_Input_APIs_with_Devices_Independent"></a>
### <a name="use-standard-input-apis-with-device-independent-calls"></a>Utiliser les API d'entrée standard avec des appels indépendants de l’appareil  
 Les appels indépendants du périphérique garantissent l’égalité des fonctionnalités du clavier et de la souris, tout en fournissant une technologie d’assistance avec les informations nécessaires sur l’interface utilisateur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Automation.Peers>
- [Contrôle personnalisé NumericUpDown avec thème et prise en charge d'UI Automation, exemple](/previous-versions/dotnet/netframework-3.5/ms771573(v=vs.90))
- [Recommandations en matière de conception d’interface utilisateur clavier](/previous-versions/windows/desktop/dnacc/guidelines-for-keyboard-user-interface-design)
