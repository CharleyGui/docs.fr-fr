---
title: Mise à l’échelle automatique
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 96dbbb5ed20027e25f1bde89748710766ec06506
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732377"
---
# <a name="automatic-scaling-in-windows-forms"></a>Mise à l’échelle automatique dans Windows Forms

La mise à l’échelle automatique permet d’afficher correctement un formulaire et ses contrôles conçus sur un ordinateur avec une certaine police système et une certaine résolution d’affichage sur un autre ordinateur avec une police système ou une résolution d’affichage différente. Elle garantit que le formulaire et ses contrôles seront redimensionnés intelligemment et de manière cohérente avec les fenêtres natives et d'autres applications sur les ordinateurs des utilisateurs et d'autres développeurs. La prise en charge des .NET Framework pour la mise à l’échelle automatique et les styles visuels permet .NET Framework applications de conserver une apparence cohérente par rapport aux applications Windows natives sur l’ordinateur de chaque utilisateur.

Dans la plupart des cas, la mise à l’échelle automatique fonctionne comme prévu dans .NET Framework version 2,0 et versions ultérieures. Toutefois, les modifications de schéma de police peuvent être problématiques. Pour obtenir un exemple de résolution de ce type, consultez [Comment : répondre aux modifications de jeu de polices dans une Application Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Nécessité d’une mise à l’échelle automatique

Sans mise à l'échelle automatique, une application conçue pour une résolution d'écran ou une police particulière apparaîtra trop petite ou trop grande en cas de modification de cette résolution ou police. Par exemple, si l'application est conçue à l'aide de la police Tahoma 9 points comme ligne de base, sans réglage elle apparaîtra trop petite si vous l'exécutez sur un ordinateur où la police système est Tahoma 12 points. Les éléments de texte (tels que les titres, les menus, le contenu des zones de texte et ainsi de suite) apparaîtront plus petits que dans les autres applications. En outre, la taille des éléments d'interface utilisateur qui contiennent du texte (comme la barre de titre, les menus et de nombreux contrôles) dépend de la police utilisée. Dans cet exemple, ces éléments apparaîtront aussi relativement plus petits.

Une situation analogue se produit quand une application est conçue pour une certaine résolution d'écran. La résolution d’affichage la plus courante est 96 points par pouce (DPI), ce qui équivaut à une mise à l’échelle d’affichage de 100%, mais les affichages de plus haute résolution prennent en charge 125%, 150%, 200% (respectivement les 120, 144 et 192 PPP) et les versions ultérieures sont devenues plus courantes. Sans réglage, une application (en particulier basée sur des graphismes) conçue pour une résolution spécifique apparaîtra trop grande ou trop petite en cas d'exécution dans une autre résolution.

La mise à l'échelle automatique vise à améliorer ces problèmes en redimensionnant automatiquement le formulaire et ses contrôles enfants en fonction de la taille de police ou résolution d'affichage relative. Le système d'exploitation Windows prend en charge la mise à l'échelle automatique des boîtes de dialogue à l'aide d'une unité de mesure relative appelée unité de boîte de dialogue. Une unité de boîte de dialogue est basée sur la police système et sa relation aux pixels peut être déterminée à l'aide de la fonction du SDK Win32 `GetDialogBaseUnits`. Quand un utilisateur change le thème utilisé par Windows, toutes les boîtes de dialogue sont automatiquement ajustés en conséquence. En outre, le .NET Framework prend en charge la mise à l’échelle automatique en fonction de la police système par défaut ou de la résolution d’affichage. Le cas échéant, la mise à l'échelle automatique peut être désactivée dans une application.

## <a name="original-support-for-automatic-scaling"></a>Prise en charge d’origine de la mise à l’échelle automatique

Les versions 1,0 et 1,1 du .NET Framework pris en charge la mise à l’échelle automatique d’une manière simple qui dépendait de la police Windows par défaut utilisée pour l’interface utilisateur, représentée par la valeur **DEFAULT_GUI_FONT**du kit de développement logiciel (SDK) Win32. Cette police est généralement modifiée uniquement quand la résolution d’écran change. Le mécanisme suivant était utilisé pour implémenter la mise à l'échelle automatique :

1. Au moment du design, la propriété <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (qui est maintenant déconseillée) prenait comme valeur la hauteur et la largeur de la police système par défaut sur l'ordinateur du développeur.

2. Au moment de l'exécution, la police système par défaut de l'ordinateur de l'utilisateur était utilisée pour initialiser la propriété <xref:System.Windows.Forms.Control.Font%2A> de la classe <xref:System.Windows.Forms.Form>.

3. Avant d'afficher le formulaire, la méthode <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> était appelée pour mettre à l'échelle le formulaire. Cette méthode calculait les tailles d'échelle relatives à partir des propriétés <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> et <xref:System.Windows.Forms.Control.Font%2A>, puis appelait la méthode <xref:System.Windows.Forms.Control.Scale%2A> pour mettre à l'échelle le formulaire et ses enfants.

4. La valeur de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> était mise à jour pour que les appels ultérieurs à <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> ne redimensionnent pas progressivement le formulaire.

Même si ce mécanisme était suffisant dans la plupart des cas, il souffrait des limitations suivantes :

- Étant donné que la propriété <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> représente la taille de police de base sous forme de valeurs entières, des erreurs d’arrondi apparaissent clairement quand un formulaire passe par plusieurs résolutions.

- La mise à l'échelle automatique était implémentée uniquement dans la classe <xref:System.Windows.Forms.Form>, et non dans la classe <xref:System.Windows.Forms.ContainerControl>. Ainsi, les contrôles utilisateur étaient mis à l’échelle correctement uniquement quand le contrôle utilisateur était conçu à la même résolution que le formulaire et quand il était placé dans le formulaire au moment du design.

- Les formulaires et leurs contrôles enfants pouvaient uniquement être conçus simultanément par plusieurs développeurs si la résolution de leurs ordinateurs était identique. De même, cela rendait l’héritage d’un formulaire dépendant de la résolution associée au formulaire parent.

- Il n’est pas compatible avec les gestionnaires de mise en page plus récents introduits avec la version 2,0 de .NET Framework, tels que <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel>.

- Il ne prenait pas en charge la mise à l’échelle basée directement sur la résolution d’affichage requise pour la compatibilité avec le .NET Compact Framework.

Bien que ce mécanisme soit conservé dans la version 2,0 de .NET Framework pour assurer la compatibilité descendante, il a été remplacé par le mécanisme de mise à l’échelle plus fiable décrit ci-après. Par conséquent, <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> et certaines surcharges <xref:System.Windows.Forms.Control.Scale%2A> sont marquées comme obsolètes.

> [!NOTE]
> Vous pouvez supprimer sans risque les références à ces membres quand vous mettez à niveau votre code hérité vers le .NET Framework version 2,0.

## <a name="current-support-for-automatic-scaling"></a>Prise en charge actuelle de la mise à l’échelle automatique

La version 2,0 de .NET Framework surmonte les limitations précédentes en introduisant les modifications suivantes de la mise à l’échelle automatique des Windows Forms :

- La prise en charge de base de la mise à l'échelle a été déplacée vers la classe <xref:System.Windows.Forms.ContainerControl> pour que les formulaires, les contrôles composites natifs et les contrôles utilisateur bénéficient tous d'une prise en charge uniforme de la mise à l'échelle. Les nouveaux membres <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> et <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> ont été ajoutés.

- La classe <xref:System.Windows.Forms.Control> comporte également plusieurs nouveaux membres qui lui permettent de participer à la mise à l'échelle et de prendre en charge la mise à l'échelle mixte sur le même formulaire. En particulier les membres <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, et <xref:System.Windows.Forms.Control.GetScaledBounds%2A> prennent en charge la mise à l'échelle.

- La prise en charge de la mise à l'échelle en fonction de la résolution d'écran a été ajoutée pour compléter la prise en charge de la police système, comme défini par l'énumération <xref:System.Windows.Forms.AutoScaleMode>. Ce mode est compatible avec la mise à l’échelle automatique prise en charge par le .NET Compact Framework facilitant la migration des applications.

- La compatibilité avec les gestionnaires de présentation tels que <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> a été ajoutée à l'implémentation de la mise à l'échelle automatique.

- Les facteurs d'échelle sont désormais représentés sous forme de valeurs à virgule flottante, généralement avec la structure <xref:System.Drawing.SizeF>. Les erreurs d'arrondi sont donc pratiquement inexistantes.

> [!CAUTION]
> Les combinaisons arbitraires de modes de mise à l'échelle de police et PPP ne sont pas prises en charge. Bien que vous puissiez mettre à l'échelle un contrôle utilisateur à l'aide d'un mode (par exemple PPP) et le et placer sur un formulaire à l'aide d'un autre mode (Police) sans problème, le fait de combiner un formulaire de base dans un mode et un formulaire dérivé dans un autre peut produire des résultats inattendus.

### <a name="automatic-scaling-in-action"></a>Mise à l’échelle automatique en action

Windows Forms utilise désormais la logique suivante pour mettre automatiquement à l'échelle les formulaires et leur contenu :

1. Au moment du design, chaque <xref:System.Windows.Forms.ContainerControl> enregistre le mode de mise à l'échelle et sa résolution actuelle dans les propriétés <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> et <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, respectivement.

2. Au moment de l’exécution, la résolution réelle est stockée dans la propriété <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A>. La propriété <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> calcule dynamiquement le rapport entre la résolution de mise à l’échelle au moment de l’exécution et au moment du design.

3. Quand le formulaire se charge, si les valeurs de <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> et <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> sont différentes, la méthode <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> est appelée pour mettre à l'échelle le contrôle et ses enfants. Cette méthode suspend la disposition et appelle la méthode <xref:System.Windows.Forms.Control.Scale%2A> pour effectuer la mise à l'échelle. Par la suite, la valeur de <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> est mise à jour pour éviter la mise à l'échelle progressive.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> est également appelée automatiquement dans les situations suivantes :

    - En réponse à l'événement <xref:System.Windows.Forms.Control.OnFontChanged%2A> si le mode de mise à l'échelle est <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Quand la disposition du contrôle conteneur reprend et qu'une modification est détectée dans la propriété <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> ou <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>.

    - Comme expliqué ci-dessus, quand un <xref:System.Windows.Forms.ContainerControl> parent est mis à l'échelle. Chaque contrôle conteneur est responsable de la mise à l'échelle de ses enfants à l'aide de ses propres facteurs d'échelle, et non de celui de son conteneur parent.

5. Les contrôles enfants peuvent modifier leur comportement de mise à l'échelle de plusieurs manières :

    - La propriété <xref:System.Windows.Forms.Control.ScaleChildren%2A> peut être substituée pour déterminer si leurs contrôles enfants doivent être mis à l'échelle ou non.

    - La méthode <xref:System.Windows.Forms.Control.GetScaledBounds%2A> peut être substituée pour ajuster les limites de mise à l'échelle du contrôle, mais pas la logique de mise à l'échelle.

    - La méthode <xref:System.Windows.Forms.Control.ScaleControl%2A> peut être substituée pour modifier la logique de mise à l'échelle pour le contrôle actuel.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Rendu des contrôles avec les styles visuels](./controls/rendering-controls-with-visual-styles.md)
- [Guide pratique pour améliorer les performances en évitant la mise à l’échelle automatique](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
