---
title: Windows Forms Add, élément de Configuration
ms.date: 04/07/2017
helpviewer_keywords:
- Windows Forms Add configuration element
- configuring Windows Forms applications
ms.assetid: 3e3e04de-99d1-4658-b716-44cb669d9589
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75a66ee7ca1d7c99de6e2cc9a1d502ea58dbf9f7
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422824"
---
# <a name="windows-forms-add-configuration-element"></a>Windows Forms Add, élément de Configuration

Le `<add>` élément ajoute une clé prédéfinie qui spécifie si votre application Windows Form prend en charge les fonctionnalités ajoutées à des applications Windows Forms dans le .NET Framework 4.7 ou version ultérieure.

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
| `key`     | Attribut requis. Nom de clé prédéfini qui correspond à une fonctionnalité personnalisable particulière de Windows Forms. |
| `value`   | Attribut requis. La valeur à assigner à `key`. |

### <a name="key-attribute-names-and-associated-values"></a>`key` noms d’attributs et valeurs associées

| `key` Nom | Valeurs | Description |
| ---------- | ------ | ----------- |
| "AnchorLayout.DisableSinglePassControlScaling" | "true"&#124;"false" | Indique si les contrôles ancrés sont mis à l’échelle en un seul passage. « true » pour désactiver unique passer mise à l’échelle ; Sinon, false. Consultez la section « Unique pass mise à l’échelle » dans le [remarques](#remarks) pour plus d’informations. |
| « DpiAwareness » | "PerMonitorV2"&#124;"false" | Indique si une application prend en charge DPI. Définissez la clé à « PerMonitorV2 » pour prendre en charge de la prise en charge Dpi ; Sinon, affectez-lui la valeur « false ». Prise en charge DPI est une fonctionnalité d’abonnement ; Pour tirer parti de la prise en charge DPI élevée de Windows Forms, vous devez définir sa valeur à « PerMonitorV2 ». Consultez le [notes](#remarks) section pour plus d’informations. |
| "CheckedListBox.DisableHighDpiImprovements" | "true"&#124;"false" | Indique si le <xref:System.Windows.Forms.CheckedListBox> contrôle tire parti de la mise à l’échelle et la disposition des améliorations introduites dans le .NET Framework 4.7. « true » pour désactiver les améliorations de mise à l’échelle et de disposition ; Sinon, « false ». |
| "DataGridView.DisableHighDpiImprovements" | "true"&#124;"false" | Indique si le <xref:System.Windows.Forms.DataGridView> contrôler la mise à l’échelle et la disposition des améliorations introduites dans le .NET Framework 4.7. « true » pour désactiver la prise en charge DPI ; « false » dans le cas contraire. |
| "DisableDpiChangedMessageHandling" | "true"&#124;"false" | « true » pour désactiver la réception des messages relatifs à la résolution de mise à l’échelle des modifications ; « false » dans le cas contraire. Consultez le [notes](#remarks) section pour plus d’informations. |
| "EnableWindowsFormsHighDpiAutoResizing" | "true"&#124;"false" | Indique si une application Windows Forms est automatiquement redimensionnée en raison de modifications de mise à l’échelle PPP. « true » pour activer le redimensionnement automatique ; Sinon, false. |
| "Form.DisableSinglePassControlScaling" | "true"&#124;"false" | Indique si le <xref:System.Windows.Forms.Form> est mis à l’échelle en un seul passage. seul-passage « true » pour désactiver la mise à l’échelle ; Sinon, false. Consultez la section « Unique pass mise à l’échelle » dans le [remarques](#remarks) pour plus d’informations. |
| "MonthCalendar.DisableSinglePassControlScaling" | "true"&#124;"false" | Indique si le <xref:System.Windows.Forms.MonthCalendar> contrôle est mis à l’échelle en un seul passage. seul-passage « true » pour désactiver la mise à l’échelle ; Sinon, false. Consultez la section « Unique pass mise à l’échelle » dans le [remarques](#remarks) pour plus d’informations. |
| "Toolstrip.DisableHighDpiImprovements" | "true"&#124;"false" | Indique si le <xref:System.Windows.Forms.ToolStrip> contrôle tire parti de la mise à l’échelle et la disposition des améliorations introduites dans le .NET Framework 4.7. « true » pour désactiver la prise en charge DPI ; « false » dans le cas contraire. |

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

| Élément | Description |
| ------- | ----------- |
| [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md) | Configure la prise en charge des nouvelles fonctionnalités d’application Windows Forms. |

## <a name="remarks"></a>Notes

À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.

Le `<System.Windows.Forms.ApplicationConfigurationSection>` élément vous permet d’ajouter un ou plusieurs enfants `<add>` éléments, chacun d’eux définit un paramètre de configuration spécifique.

Pour une vue d’ensemble de la prise en charge Windows Forms haute résolution, consultez [prennent en charge DPI d’élevé dans les Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="dpiawareness"></a>DpiAwareness

Les applications Windows Forms qui fonctionnent sous les versions de Windows à partir de Windows 10 Creators Edition et cibler des versions du .NET Framework en commençant par le .NET Framework 4.7 peuvent être configurées pour tirer parti des améliorations de PPP élevées introduite dans le .NET Framework 4.7. Elles incluent notamment :

- Prise en charge pour les scénarios de résolution dynamiques dans lequel l’utilisateur modifie le facteur de PPP ou mise à l’échelle après le lancement d’une application Windows Forms.

- Améliorations de la mise à l’échelle et la disposition d’un nombre de Windows Forms des contrôles, tels que le <xref:System.Windows.Forms.MonthCalendar> contrôle et le <xref:System.Windows.Forms.CheckedListBox> contrôle.

Prise en charge DPI élevé est une fonctionnalité d’abonnement ; par défaut, la valeur de `DpiAwareness` est `false`. Vous pouvez opter pour prise en charge des Windows Forms pour la prise en charge DPI en définissant la valeur de cette clé à `PerMonitorV2` dans le fichier de configuration d’application. Si la prise en charge DPI est activée, toutes les fonctionnalités de PPP individuelles sont également activées. Elles incluent notamment :

- PPP modifié des messages, qui sont contrôlées par le `DisableDpiChangedMessageHandling` clé.

- PPP prise en charge dynamique, qui est contrôlé par le `EnableWindowsFormsHighDpiAutoResizing` clé.

- Seul passage mise à l’échelle du contrôle, qui est contrôlé par le `Form.DisableSinglePassControlScaling` de chaque <xref:System.Windows.Forms.Form> des contrôles, en le `AnchorLayout.DisableSinglePassControlScaling` clés pour les contrôles ancrés et par le `MonthCalendar.DisableSinglePassControlScaling` clés pour le <xref:System.Windows.Forms.MonthCalendar> contrôle

- Haute résolution mise à l’échelle et la disposition améliorations, qui est contrôlé par le `CheckListBox.DisableHighDpiImprovements` clés pour le <xref:System.Windows.Forms.CheckedListBox> contrôler, par le `DataGridView.DisableHighDpiImprovements` clés pour le <xref:System.Windows.Forms.DataGridView> contrôle et par le `Toolstrip.DisableHighDpiImprovements` clé pour la le <xref:System.Windows.Forms.ToolStrip> contrôle.

Le paramètre de participer unique par défaut fourni par le paramètre `DpiAwareness` à `PerMonitorV2` est généralement suffisant pour les nouvelles applications Windows Forms. Toutefois, vous pouvez ensuite refuser individuelles améliorations PPP élevées en ajoutant la clé correspondante dans le fichier de configuration d’application. Par exemple, pour tirer parti de toutes les fonctionnalités de résolution nouveau à l’exception de prise en charge de résolution dynamique, vous devez ajouter les éléments suivants au fichier de configuration de votre application :

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
   <add key="DpiAwareness" value="PerMonitorV2" />
   <!-- Disable dynamic DPI support -->
   <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

En règle générale, vous refuser une fonctionnalité particulière, car vous avez choisi de le gérer par programmation.

Pour plus d’informations en tirant profit de prise en charge de la haute résolution dans les applications Windows Forms, consultez [prennent en charge DPI d’élevé dans les Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md).

### <a name="disabledpichangedmessagehandling"></a>DisableDpiChangedMessageHandling

À compter de .NET Framework 4.7, contrôles Windows Forms déclenchent un nombre d’événements liés aux modifications dans la mise à l’échelle PPP. Ceux-ci incluent le <xref:System.Windows.Forms.Control.DpiChangedAfterParent>, <xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, et <xref:System.Windows.Forms.Form.DpiChanged> événements. La valeur de la `DisableDpiChangedMessageHandling` clé détermine si ces événements sont déclenchés dans une application Windows Forms.

### <a name="single-pass-scaling"></a>Mise à l’échelle de transmission unique

La mise à l’échelle unique ou multipasse influence la réactivité perçue de l’interface utilisateur et l’apparence visuelle des éléments d’interface utilisateur comme ils sont mis à l’échelle. À compter de .NET Framework 4.7, Windows Forms utilise mise à l’échelle d’une seule passe. Dans les versions précédentes du .NET Framework, la mise à l’échelle a été effectuée via plusieurs passes, ce qui a provoqué des contrôles à l’échelle plus de données nécessaires. Mise à l’échelle de transmission unique doit être désactivé uniquement si votre application dépend de l’ancien comportement.

## <a name="see-also"></a>Voir aussi

- [Section de configuration de Windows Forms](../../../../../docs/framework/configure-apps/file-schema/winforms/index.md)
- [Prise en charge de la haute résolution dans Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
