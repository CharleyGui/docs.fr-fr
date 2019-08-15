---
title: Paramètres d'application pour les contrôles personnalisés
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040458"
---
# <a name="application-settings-for-custom-controls"></a>Paramètres d'application pour les contrôles personnalisés
Vous devez effectuer certaines tâches pour permettre à vos contrôles personnalisés de conserver les paramètres d’application lorsque les contrôles sont hébergés dans des applications tierces.

 La majeure partie de la documentation relative à la fonctionnalité des paramètres d’application est écrite en supposant que vous créez une application autonome. Toutefois, si vous créez un contrôle que d’autres développeurs hébergeront dans leurs applications, vous devez effectuer quelques étapes supplémentaires pour que votre contrôle conserve correctement ses paramètres.

## <a name="application-settings-and-custom-controls"></a>Paramètres d’application et contrôles personnalisés
 Pour que votre contrôle conserve correctement ses paramètres, il doit encapsuler le processus en créant sa propre classe wrapper de paramètres d’applications dédiées, dérivée de <xref:System.Configuration.ApplicationSettingsBase>. En outre, la classe de contrôle principale doit implémenter <xref:System.Configuration.IPersistComponentSettings>. L’interface contient plusieurs propriétés, ainsi que deux méthodes, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> et <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Si vous ajoutez votre contrôle à un formulaire à l’aide du **Concepteur Windows Forms** dans Visual Studio, Windows Forms <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> appellera automatiquement lorsque le contrôle est initialisé; vous devez vous <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> appeler dans la `Dispose` méthode de votre contrôle.

 En outre, vous devez implémenter les éléments suivants pour que les paramètres d’application des contrôles personnalisés fonctionnent correctement dans les environnements au moment du design, tels que Visual Studio:

1. Classe de paramètres d’application personnalisée avec un constructeur qui accepte <xref:System.ComponentModel.IComponent> un comme paramètre unique. Utilisez cette classe pour enregistrer et charger tous les paramètres de votre application. Quand vous créez une nouvelle instance de cette classe, vous devez passer votre contrôle personnalisé à l’aide du constructeur.

2. Créez cette classe de paramètres personnalisée une fois que le contrôle a été créé et placé sur un formulaire, par exemple dans <xref:System.Windows.Forms.Form.Load> le gestionnaire d’événements du formulaire.

 Pour obtenir des instructions sur la création d’une classe [de paramètres personnalisés, consultez Procédure: Créer des paramètres](how-to-create-application-settings.md)d’application.

## <a name="settings-keys-and-shared-settings"></a>Clés de paramètres et paramètres partagés
 Certains contrôles peuvent être utilisés plusieurs fois dans le même formulaire. La plupart du temps, vous voudrez que ces contrôles conservent leurs propres paramètres individuels. Lorsque la <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> propriété est <xref:System.Configuration.IPersistComponentSettings>activée, vous pouvez fournir une chaîne unique qui agit pour lever l’ambiguïté entre plusieurs versions d’un contrôle sur un formulaire.

 La façon la plus simple d' <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> implémenter consiste à <xref:System.Windows.Forms.Control.Name%2A> utiliser la propriété <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>du contrôle pour. Lorsque vous chargez ou enregistrez les paramètres du contrôle, vous transmettez la <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> valeur de à <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> la propriété de <xref:System.Configuration.ApplicationSettingsBase> la classe. Les paramètres d’application utilisent cette clé unique lorsqu’il conserve les paramètres de l’utilisateur au format XML. L’exemple de code suivant montre comment `<userSettings>` une section peut rechercher une instance d’un contrôle personnalisé nommé `CustomControl1` qui enregistre un paramètre pour sa `Text` propriété.

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 Toutes les instances d’un contrôle qui ne fournissent pas de valeur <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> pour partagent les mêmes paramètres.

## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Architecture des paramètres d'application](application-settings-architecture.md)
