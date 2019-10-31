---
title: Windows Forms ajouter un élément de configuration
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
ms.openlocfilehash: 26b806f84c3e1bc44e0437a8f8806316b14897b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109662"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms ajouter un élément de configuration

L’élément `<add>` ajoute une clé prédéfinie qui spécifie si votre application Windows Form prend en charge les fonctionnalités ajoutées aux applications Windows Forms dans le .NET Framework 4,7 ou version ultérieure.

## <a name="syntax"></a>Syntaxe

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="key-name" value="key-value" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

| Attribut | Description |
| --------- | ----------- |
| `key`     | Attribut requis. Nom de clé prédéfini qui correspond à une fonctionnalité spécifique Windows Forms personnalisable. |
| `value`   | Attribut requis. Valeur à assigner à `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key` des noms d’attributs et des valeurs associées

| Nom `key` | Valeurs | Description |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | « true »&#124;« false » | Indique si les contrôles ancrés sont mis à l’échelle en une seule passe. « true » pour désactiver la mise à l’échelle avec un seul passage ; Sinon, false. Pour plus d’informations, consultez la section « mise à l’échelle à passage unique » dans les [Notes](#remarks) . |
| "DpiAwareness" | « PerMonitorV2 »&#124;« false » | Indique si une application prend en charge DPI. Définissez la clé sur « PerMonitorV2 » pour prendre en charge la reconnaissance dpi ; Sinon, affectez-lui la valeur « false ». La reconnaissance DPI est une fonctionnalité d’abonnement. pour tirer parti de la prise en charge de la haute résolution Windows Forms, vous devez définir sa valeur sur « PerMonitorV2 ». Pour plus d’informations, consultez la section [Notes](#remarks) . |
| « CheckedListBox. DisableHighDpiImprovements » | « true »&#124;« false » | Indique si le contrôle de <xref:System.Windows.Forms.CheckedListBox> tire parti des améliorations apportées à la mise à l’échelle et à la disposition introduites dans le .NET Framework 4,7. « true » pour refuser les améliorations de la mise à l’échelle et de la disposition ; Sinon, « false ». |
| « DataGridView. DisableHighDpiImprovements » | « true »&#124;« false » | Indique si le <xref:System.Windows.Forms.DataGridView> contrôlent les améliorations apportées à la mise à l’échelle et à la disposition dans la .NET Framework 4,7. « true » pour refuser la prise en charge de DPI ; « false » dans le cas contraire. |
| "DisableDpiChangedMessageHandling" | « true »&#124;« false » | « true » pour refuser de recevoir les messages liés aux modifications de mise à l’échelle DPI ; « false » dans le cas contraire. Pour plus d’informations, consultez la section [Notes](#remarks) . |
| "EnableWindowsFormsHighDpiAutoResizing" | « true »&#124;« false » | Indique si une application Windows Forms est automatiquement redimensionnée en raison de modifications de mise à l’échelle DPI. « true » pour activer le redimensionnement automatique ; Sinon, false. |
| « Form. DisableSinglePassControlScaling » | « true »&#124;« false » | Indique si la <xref:System.Windows.Forms.Form> est mise à l’échelle en une seule passe. « true » pour désactiver la mise à l’échelle à passage simple ; Sinon, false. Pour plus d’informations, consultez la section « mise à l’échelle à passage unique » dans les [Notes](#remarks) . |
| "MonthCalendar. DisableSinglePassControlScaling" | « true »&#124;« false » | Indique si le contrôle de <xref:System.Windows.Forms.MonthCalendar> est mis à l’échelle en une seule passe. « true » pour désactiver la mise à l’échelle à passage simple ; Sinon, false. Pour plus d’informations, consultez la section « mise à l’échelle à passage unique » dans les [Notes](#remarks) . |
| « ToolStrip. DisableHighDpiImprovements » | « true »&#124;« false » | Indique si le contrôle de <xref:System.Windows.Forms.ToolStrip> tire parti des améliorations apportées à la mise à l’échelle et à la disposition introduites dans le .NET Framework 4,7. « true » pour refuser la prise en charge de DPI ; « false » dans le cas contraire. |

### <a name="child-elements"></a>Éléments enfants

Aucun(e).

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](index.md) | Configure la prise en charge des nouvelles fonctionnalités de l’application Windows Forms. |

## <a name="remarks"></a>Notes

À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.

L’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet d’ajouter un ou plusieurs éléments de `<add>` enfants, chacun d’eux définissant un paramètre de configuration spécifique.

Pour obtenir une vue d’ensemble de la prise en charge de Windows Forms haute résolution, consultez [prise en charge des résolutions élevées dans Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Windows Forms les applications qui s’exécutent sous les versions de Windows à partir de Windows 10 Creators Edition et les versions cibles du .NET Framework à compter de la .NET Framework 4,7 peuvent être configurées pour tirer parti des améliorations haute résolution introduites dans le .NET Framework 4,7. Elles incluent notamment les suivantes :

- Prise en charge des scénarios PPP dynamiques dans lesquels l’utilisateur modifie la résolution ou le facteur d’échelle après le lancement d’une application Windows Forms.

- Améliorations de la mise à l’échelle et de la disposition d’un certain nombre de contrôles Windows Forms, tels que le contrôle <xref:System.Windows.Forms.MonthCalendar> et le contrôle <xref:System.Windows.Forms.CheckedListBox>.

La reconnaissance haute résolution est une fonctionnalité d’abonnement. par défaut, la valeur de `DpiAwareness` est `false`. Vous pouvez opter pour la prise en charge d’Windows Forms pour la prise en charge de DPI en définissant la valeur de cette clé sur `PerMonitorV2` dans le fichier de configuration de l’application. Si la reconnaissance DPI est activée, toutes les fonctionnalités PPP individuelles sont également activées. Elles incluent notamment les suivantes :

- PPP messages modifiés, qui sont contrôlés par la clé de `DisableDpiChangedMessageHandling`.

- La prise en charge de PPP dynamique, qui est contrôlée par la clé de `EnableWindowsFormsHighDpiAutoResizing`.

- Mise à l’échelle du contrôle à passage unique, qui est contrôlée par le `Form.DisableSinglePassControlScaling` pour les contrôles <xref:System.Windows.Forms.Form> individuels, par la clé de `AnchorLayout.DisableSinglePassControlScaling` pour les contrôles ancrés et par la clé de `MonthCalendar.DisableSinglePassControlScaling` pour le contrôle <xref:System.Windows.Forms.MonthCalendar>

- Améliorations de la mise à l’échelle et de la disposition haute résolution, qui sont contrôlées par la clé de `CheckListBox.DisableHighDpiImprovements` pour le contrôle <xref:System.Windows.Forms.CheckedListBox>, par la clé de `DataGridView.DisableHighDpiImprovements` pour le contrôle <xref:System.Windows.Forms.DataGridView> et par la clé `Toolstrip.DisableHighDpiImprovements` pour le contrôle <xref:System.Windows.Forms.ToolStrip>.

Le paramètre d’abonnement par défaut unique fourni par la définition de `DpiAwareness` à `PerMonitorV2` est généralement adapté aux nouvelles applications de Windows Forms. Toutefois, vous pouvez ensuite refuser des améliorations de haute résolution, en ajoutant la clé correspondante au fichier de configuration de l’application. Par exemple, pour tirer parti de toutes les nouvelles fonctionnalités PPP, à l’exception de la prise en charge de la résolution dynamique PPP, ajoutez ce qui suit à votre fichier de configuration d’application :

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

En règle générale, vous désabonnez une fonctionnalité particulière, car vous avez choisi de la gérer par programmation.

Pour plus d’informations sur la prise en charge de la haute résolution dans les applications Windows Forms, consultez [prise en charge des résolutions élevées dans Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md).

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

À partir de la .NET Framework 4,7, Windows Forms contrôles déclenchent un certain nombre d’événements liés aux modifications de la mise à l’échelle DPI. Il s’agit notamment des événements <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>et <xref:System.Windows.Forms.Form.DpiChanged>. La valeur de la clé de `DisableDpiChangedMessageHandling` détermine si ces événements sont déclenchés dans une application Windows Forms.

### <a name="single-pass-scaling"></a>Mise à l’échelle à passage unique

La mise à l’échelle à une ou plusieurs passes influence la réactivité perçue de l’interface utilisateur et l’apparence visuelle des éléments de l’interface utilisateur à mesure qu’ils sont mis à l’échelle. À partir de la .NET Framework 4,7, Windows Forms utilise la mise à l’échelle à passage unique. Dans les versions précédentes de la .NET Framework, la mise à l’échelle a été effectuée par le biais de plusieurs passes, ce qui a entraîné une mise à l’échelle de certains contrôles plus que nécessaire. La mise à l’échelle avec une seule passe doit être désactivée uniquement si votre application dépend de l’ancien comportement.

## <a name="see-also"></a>Voir aussi

- [Section de configuration de Windows Forms](index.md)
- [Prise en charge de la haute résolution dans Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
