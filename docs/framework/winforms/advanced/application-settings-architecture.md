---
title: Architecture des paramètres d'application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: b5d5a4456bef925cd8093fe9c696145aff83660e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039418"
---
# <a name="application-settings-architecture"></a>Architecture des paramètres d'application
Cette rubrique décrit le fonctionnement de l’architecture Paramètres d’application et explore des fonctionnalités avancées de l’architecture telles que les paramètres groupés et les clés de paramètres.

 L’architecture des paramètres d’application prend en charge la définition des paramètres fortement typés avec l’application ou la portée utilisateur, et la persistance des paramètres entre les sessions d’application. L’architecture fournit un moteur de persistance par défaut pour enregistrer les paramètres et les charger à partir du système de fichiers local. L’architecture définit également les interfaces qui fournissent un moteur de persistance personnalisé.

 Des interfaces sont fournies afin de permettre aux composants personnalisés de conserver leurs propres paramètres lorsqu’ils sont hébergés dans une application. À l’aide de clés de paramètres, les composants peuvent séparer les paramètres pour plusieurs instances du composant.

## <a name="defining-settings"></a>Définition des paramètres
 L’architecture des paramètres d’application est utilisée dans ASP.NET et Windows Forms, et elle contient un certain nombre de classes de base qui sont partagées entre les deux environnements. Le plus important est <xref:System.Configuration.SettingsBase>, qui fournit l’accès aux paramètres via une collection et fournit des méthodes de bas niveau pour le chargement et l’enregistrement des paramètres. Chaque environnement implémente sa propre classe dérivée <xref:System.Configuration.SettingsBase> de pour fournir des fonctionnalités de paramètres supplémentaires pour cet environnement. Dans une application basée sur Windows Forms, tous les paramètres d’application doivent être définis sur une classe dérivée de la <xref:System.Configuration.ApplicationSettingsBase> classe, ce qui ajoute les fonctionnalités suivantes à la classe de base:

- Chargement et enregistrement d’opérations de plus haut niveau

- Prise en charge des paramètres de portée utilisateur

- Rétablissement des paramètres d’un utilisateur aux valeurs par défaut

- Mise à niveau des paramètres à partir d’une version précédente de l’application

- Validation des paramètres, avant leur modification ou leur enregistrement

 Les paramètres peuvent être décrits à l’aide d’un certain nombre d' <xref:System.Configuration> attributs définis dans l’espace de noms. ceux-ci sont décrits dans [attributs des paramètres d’application](application-settings-attributes.md). Lorsque vous définissez un paramètre, vous devez l’appliquer avec <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, ce qui indique si le paramètre s’applique à l’application entière ou uniquement à l’utilisateur actuel.

 L’exemple de code suivant définit une classe de paramètres personnalisés avec un paramètre unique, `BackgroundColor`.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Persistance des paramètres
 La <xref:System.Configuration.ApplicationSettingsBase> classe ne conserve pas elle-même les paramètres, mais cette tâche s’applique au fournisseur de paramètres, une classe qui <xref:System.Configuration.SettingsProvider>dérive de. Si une classe dérivée <xref:System.Configuration.ApplicationSettingsBase> de ne spécifie pas de fournisseur de <xref:System.Configuration.SettingsProviderAttribute>paramètres via, le fournisseur par <xref:System.Configuration.LocalFileSettingsProvider>défaut,, est utilisé.

 Le système de configuration qui a été publié à l’origine avec le .NET Framework prend en charge la fourniture de données de configuration d’application statiques via le `app.`fichier machine. config de l’ordinateur local ou dans un fichier exe. config que vous déployez avec votre application. La <xref:System.Configuration.LocalFileSettingsProvider> classe étend cette prise en charge native des manières suivantes:

- Les paramètres de portée d’application peuvent être stockés dans des fichiers machine.config ou `app.`exe.config. Machine.config est toujours en lecture seule, tandis que `app`.exe.config est limité par des considérations de sécurité en lecture seule pour la plupart des applications.

- Les paramètres de portée utilisateur peuvent être stockés dans des fichiers `app`.exe.config, fichiers, auquel cas ils sont traités comme des valeurs par défaut statiques.

- Les paramètres de portée utilisateur non définis par défaut sont stockés dans un nouveau fichier, *user*.config, où *user* est le nom d’utilisateur de la personne qui exécute actuellement l’application. Vous pouvez spécifier une valeur par défaut pour un paramètre de portée utilisateur <xref:System.Configuration.DefaultSettingValueAttribute>avec. Étant donné que les paramètres de portée utilisateur changent souvent pendant l’exécution d’applications, `user`.config est toujours accessible en lecture/écriture.

 Ces trois fichiers de configuration stockent les paramètres au format XML. L’élément XML de niveau supérieur pour les paramètres de portée d’application est `<appSettings>`, tandis que `<userSettings>` est utilisé pour les paramètres de portée utilisateur. Un fichier `app`.exe.config contenant les paramètres de portée d’application et les valeurs par défaut pour les paramètres de portée utilisateur ressemblerait à ceci :

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
        </sectionGroup>
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
        </sectionGroup>
    </configSections>
    <applicationSettings>
        <WindowsApplication1.Properties.Settings>
            <setting name="Cursor" serializeAs="String">
                <value>Default</value>
            </setting>
            <setting name="DoubleBuffering" serializeAs="String">
                <value>False</value>
            </setting>
        </WindowsApplication1.Properties.Settings>
    </applicationSettings>
    <userSettings>
        <WindowsApplication1.Properties.Settings>
            <setting name="FormTitle" serializeAs="String">
                <value>Form1</value>
            </setting>
            <setting name="FormSize" serializeAs="String">
                <value>595, 536</value>
            </setting>
        </WindowsApplication1.Properties.Settings>
    </userSettings>
</configuration>
```

 Pour une définition des éléments dans la section Paramètres d’application d’un fichier de configuration, consultez [Schéma des paramètres d'application](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Liaisons de paramètres
 Les paramètres d’application utilisent l’architecture de liaison de données Windows Forms pour fournir une communication bidirectionnelle pour les mises à jour des paramètres entre les composants et l’objet de paramètres. Si vous utilisez Visual Studio pour créer des paramètres d’application et les affecter aux propriétés du composant, ces liaisons sont générées automatiquement.

 Vous pouvez uniquement lier un paramètre d’application à un composant qui prend <xref:System.Windows.Forms.IBindableComponent> en charge l’interface. En outre, le composant doit implémenter un événement de modification pour une propriété liée spécifique, ou notifier les paramètres de l’application <xref:System.ComponentModel.INotifyPropertyChanged> que la propriété a changé par le biais de l’interface. Si le composant n’implémente <xref:System.Windows.Forms.IBindableComponent> pas et que vous effectuez une liaison par le biais de Visual Studio, les propriétés liées sont définies la première fois, mais elles ne sont pas mises à jour. Si le composant implémente <xref:System.Windows.Forms.IBindableComponent> , mais ne prend pas en charge les notifications de modification de propriété, la liaison ne sera pas mise à jour dans le fichier de paramètres lorsque la propriété sera modifiée.

 Certains composants de Windows Forms, tels <xref:System.Windows.Forms.ToolStripItem>que, ne prennent pas en charge les liaisons de paramètres.

### <a name="settings-serialization"></a>Sérialisation de paramètres
 Lorsque <xref:System.Configuration.LocalFileSettingsProvider> doit enregistrer les paramètres sur le disque, il effectue les actions suivantes:

1. Utilise la réflexion pour examiner toutes les propriétés définies sur votre <xref:System.Configuration.ApplicationSettingsBase> classe dérivée, en recherchant celles qui sont appliquées <xref:System.Configuration.ApplicationScopedSettingAttribute> avec <xref:System.Configuration.UserScopedSettingAttribute>ou.

2. Sérialise la propriété sur le disque. Il tente d’abord d’appeler <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> ou <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> sur le associé <xref:System.ComponentModel.TypeConverter>au type. Si cela ne réussit pas, la sérialisation XML est utilisée à la place.

3. Détermine quels paramètres vont dans quels fichiers, selon l’attribut du paramètre.

 Si vous implémentez votre propre classe de paramètres, vous pouvez <xref:System.Configuration.SettingsSerializeAsAttribute> utiliser pour marquer un paramètre pour la sérialisation binaire ou personnalisée à l' <xref:System.Configuration.SettingsSerializeAs> aide de l’énumération. Pour plus d’informations sur la création de votre propre classe de paramètres [dans le code, consultez Procédure: Créer des paramètres](how-to-create-application-settings.md)d’application.

### <a name="settings-file-locations"></a>Emplacements des fichiers de paramètres
 L’emplacement des fichiers `app`.exe.config et *user*.config varie en fonction de la façon dont l’application est installée. Pour une application Windows Forms copiée sur l’ordinateur local, `app`. exe. config se trouve dans le même répertoire que le répertoire de base du fichier exécutable principal de l’application, et *User*. config se trouve à l’emplacement spécifié par la <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> propriété. Pour une application installée par le biais de ClickOnce, ces deux fichiers se trouvent dans le répertoire de données ClickOnce sous%InstallRoot%\Documents and Settings et paramètres\\*nom d’utilisateur*\Local paramètres.

 L’emplacement de stockage de ces fichiers est légèrement différent si un utilisateur a activé les profils itinérants, ce qui permet à un utilisateur de définir différents paramètres d’application et Windows lorsqu’il utilise d’autres ordinateurs dans un domaine. Dans ce cas, les applications ClickOnce et les applications non-ClickOnce auront leurs `app`fichiers. exe. config et *User*. config stockés sous%InstallRoot%\Documents and Settings et paramètres\\*nom d’utilisateur*\Application Data.

 Pour plus d’informations sur le fonctionnement de la fonctionnalité Paramètres d’application avec la nouvelle technologie de déploiement, consultez [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings). Pour plus d’informations sur le répertoire de données ClickOnce, consultez [accès aux données locales et distantes dans les applications ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Paramètres d’application et sécurité
 Les paramètres d’application sont conçus pour fonctionner en mode de confiance partielle, un environnement restreint qui est la configuration par défaut pour les applications Windows Forms hébergées sur Internet ou sur un intranet. Aucune autorisation spéciale au-delà de la confiance partielle n’est nécessaire pour utiliser les paramètres d’application avec le fournisseur de paramètres par défaut.

 Lorsque les paramètres d’application sont utilisés dans une application ClickOnce `user`, le fichier. config est stocké dans le répertoire de données ClickOnce. La taille du fichier `user`. config de l’application ne peut pas dépasser le quota de répertoire de données défini par ClickOnce. Pour plus d'informations, consultez [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Fournisseurs de paramètres personnalisés
 Dans l’architecture des paramètres d’application, il existe un couplage faible entre la classe wrapper de paramètres d’application <xref:System.Configuration.ApplicationSettingsBase>, dérivée de, et le ou les fournisseurs de <xref:System.Configuration.SettingsProvider>paramètres associés, dérivés de. Cette association est définie uniquement par le <xref:System.Configuration.SettingsProviderAttribute> appliqué à la classe wrapper ou à ses propriétés individuelles. Si un fournisseur de paramètres n’est pas explicitement spécifié, le fournisseur <xref:System.Configuration.LocalFileSettingsProvider>par défaut,, est utilisé. Par conséquent, cette architecture prend en charge la création et l’utilisation de fournisseurs de paramètres personnalisés.

 Par exemple, supposons que vous souhaitez développer et utiliser `SqlSettingsProvider`, un fournisseur qui stockera toutes les données de paramètres dans une base de données Microsoft SQL Server. Votre <xref:System.Configuration.SettingsProvider>classe dérivée de reçoit ces informations dans sa `Initialize` méthode en tant que paramètre de <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>type. Vous devez ensuite implémenter <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> la méthode pour récupérer vos paramètres à partir du magasin de <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> données et les enregistrer. Votre fournisseur peut utiliser le <xref:System.Configuration.SettingsPropertyCollection> fourni pour <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> déterminer le nom, le type et l’étendue de la propriété, ainsi que tous les autres attributs de paramètres définis pour cette propriété.

 Votre fournisseur devra implémenter une propriété et une méthode dont les implémentations peuvent ne pas être évidentes. La <xref:System.Configuration.SettingsProvider.ApplicationName%2A> propriété est une propriété abstraite <xref:System.Configuration.SettingsProvider>de; vous devez la programmer pour retourner les éléments suivants:

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Votre classe dérivée doit également implémenter une méthode `Initialize` qui n’accepte aucun argument et ne retourne aucune valeur. Cette méthode n’est pas définie <xref:System.Configuration.SettingsProvider>par.

 Enfin, vous implémentez <xref:System.Configuration.IApplicationSettingsProvider> sur votre fournisseur pour assurer la prise en charge de l’actualisation des paramètres, le rétablissement des paramètres par défaut et la mise à niveau des paramètres d’une version d’application vers une autre.

 Une fois que vous avez implémenté et compilé votre fournisseur, vous devez demander à votre classe de paramètres d’utiliser ce fournisseur au lieu de la valeur par défaut. Pour ce faire, vous <xref:System.Configuration.SettingsProviderAttribute>pouvez utiliser le. S’il est appliqué à une classe de paramètres entière, le fournisseur est utilisé pour chaque paramètre défini par la classe; s’il est appliqué à des paramètres individuels, l’architecture des paramètres d’application utilise ce fournisseur pour <xref:System.Configuration.LocalFileSettingsProvider> ces paramètres uniquement et utilise pour le reste. L’exemple de code suivant montre comment indiquer à la classe de paramètres d’utiliser votre fournisseur personnalisé.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Un fournisseur peut être appelé à partir de plusieurs threads simultanément, mais il écrira toujours au même emplacement de stockage. Par conséquent, l’architecture de paramètres d’application n’instanciera jamais qu’une seule instance de votre classe de fournisseur.

> [!IMPORTANT]
>  Vous devez vous assurer que votre fournisseur est thread-safe et autorise un seul thread à la fois à écrire dans les fichiers de configuration.

 Votre fournisseur n’a pas besoin de prendre en charge tous les attributs de paramètres <xref:System.Configuration?displayProperty=nameWithType> définis dans l’espace de noms, même s' <xref:System.Configuration.ApplicationScopedSettingAttribute> il <xref:System.Configuration.UserScopedSettingAttribute>doit prendre en charge au <xref:System.Configuration.DefaultSettingValueAttribute>minimum et, et doit également prendre en charge. Pour les attributs qu’il ne prend pas en charge, votre fournisseur doit simplement échouer sans notification. Il ne doit pas lever une exception. Toutefois, si la classe de paramètres utilise une combinaison non valide d’attributs (comme <xref:System.Configuration.ApplicationScopedSettingAttribute> l' <xref:System.Configuration.UserScopedSettingAttribute> application de et au même paramètre), votre fournisseur doit lever une exception et cesser l’opération.

## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Vue d'ensemble des paramètres d'application](application-settings-overview.md)
- [Application Settings for Custom Controls](application-settings-for-custom-controls.md)
- [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings)
- [Schéma des paramètres d'application](../../configure-apps/file-schema/application-settings-schema.md)
