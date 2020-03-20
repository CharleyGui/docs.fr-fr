---
title: Architecture des paramètres d'application
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 078b5f3fc1cd4273af282580f41e68ca9bd8ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182625"
---
# <a name="application-settings-architecture"></a>Architecture des paramètres d'application
Cette rubrique décrit le fonctionnement de l’architecture Paramètres d’application et explore des fonctionnalités avancées de l’architecture telles que les paramètres groupés et les clés de paramètres.

 L’architecture des paramètres d’application prend en charge la définition des paramètres fortement typés avec l’application ou la portée utilisateur, et la persistance des paramètres entre les sessions d’application. L’architecture fournit un moteur de persistance par défaut pour enregistrer les paramètres et les charger à partir du système de fichiers local. L’architecture définit également les interfaces qui fournissent un moteur de persistance personnalisé.

 Des interfaces sont fournies afin de permettre aux composants personnalisés de conserver leurs propres paramètres lorsqu’ils sont hébergés dans une application. À l’aide de clés de paramètres, les composants peuvent séparer les paramètres pour plusieurs instances du composant.

## <a name="defining-settings"></a>Définition des paramètres
 L’architecture des paramètres d’application est utilisée à la fois dans ASP.NET et Windows Forms, et elle contient un certain nombre de classes de base qui sont partagées sur les deux environnements. Le plus <xref:System.Configuration.SettingsBase>important est , qui donne accès aux paramètres par le biais d’une collection, et fournit des méthodes de faible niveau pour le chargement et l’enregistrement des paramètres. Chaque environnement implémente <xref:System.Configuration.SettingsBase> sa propre classe dérivée pour fournir des fonctionnalités de paramètres supplémentaires pour cet environnement. Dans une application basée sur windows Forms, tous les paramètres <xref:System.Configuration.ApplicationSettingsBase> d’application doivent être définis sur une classe dérivée de la classe, ce qui ajoute les fonctionnalités suivantes à la classe de base :

- Chargement et enregistrement d’opérations de plus haut niveau

- Prise en charge des paramètres de portée utilisateur

- Rétablissement des paramètres d’un utilisateur aux valeurs par défaut

- Mise à niveau des paramètres à partir d’une version précédente de l’application

- Validation des paramètres, avant leur modification ou leur enregistrement

 Les paramètres peuvent être décrits à l’aide d’un certain nombre d’attributs définis dans l’espace de <xref:System.Configuration> nom; ceux-ci sont décrits dans [Paramètres d’application Attributs](application-settings-attributes.md). Lorsque vous définissez un paramètre, <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>vous devez l’appliquer avec l’un ou l’autre ou , qui décrit si le paramètre s’applique à l’ensemble de l’application ou tout simplement à l’utilisateur actuel.

 L’exemple de code suivant définit une classe de paramètres personnalisés avec un paramètre unique, `BackgroundColor`.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Persistance des paramètres
 La <xref:System.Configuration.ApplicationSettingsBase> classe ne persiste pas elle-même ou ne charge pas les paramètres; ce travail appartient au fournisseur de paramètres, <xref:System.Configuration.SettingsProvider>une classe qui dérive de . Si une catégorie <xref:System.Configuration.ApplicationSettingsBase> dérivée de ne <xref:System.Configuration.SettingsProviderAttribute>spécifie <xref:System.Configuration.LocalFileSettingsProvider>pas un fournisseur de paramètres par l’intermédiaire du fournisseur , alors le fournisseur par défaut, est utilisé.

 Le système de configuration qui a été initialement publié avec le cadre .NET prend en charge `app.`la fourniture de données de configuration d’application statiques à travers le fichier machine.config de l’ordinateur local ou dans un fichier exe.config que vous déployez avec votre application. La <xref:System.Configuration.LocalFileSettingsProvider> classe élargit ce soutien autochtone de la façon suivante :

- Les paramètres de portée d’application peuvent être stockés dans des fichiers machine.config ou `app.`exe.config. Machine.config est toujours en lecture seule, tandis que `app`.exe.config est limité par des considérations de sécurité en lecture seule pour la plupart des applications.

- Les paramètres de portée utilisateur peuvent être stockés dans des fichiers `app`.exe.config, fichiers, auquel cas ils sont traités comme des valeurs par défaut statiques.

- Les paramètres de portée utilisateur non définis par défaut sont stockés dans un nouveau fichier, *user*.config, où *user* est le nom d’utilisateur de la personne qui exécute actuellement l’application. Vous pouvez spécifier un défaut <xref:System.Configuration.DefaultSettingValueAttribute>pour un paramètre à portée utilisateur avec . Étant donné que les paramètres de portée utilisateur changent souvent pendant l’exécution d’applications, `user`.config est toujours accessible en lecture/écriture.

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

 Vous ne pouvez lier un paramètre <xref:System.Windows.Forms.IBindableComponent> d’application qu’à un composant qui prend en charge l’interface. En outre, le composant doit implémenter un événement de modification pour une <xref:System.ComponentModel.INotifyPropertyChanged> propriété liée spécifique, ou aviser les paramètres d’application que la propriété a changé à travers l’interface. Si le composant <xref:System.Windows.Forms.IBindableComponent> ne s’implémente pas et que vous reliez Visual Studio, les propriétés liées seront définies la première fois, mais ne seront pas mises à jour. Si le composant <xref:System.Windows.Forms.IBindableComponent> implémente mais ne prend pas en charge les notifications de modification de propriété, la liaison ne sera pas mise à jour dans le fichier des paramètres lorsque la propriété est modifiée.

 Certains composants de formulaires <xref:System.Windows.Forms.ToolStripItem>Windows, tels que , ne prennent pas en charge les paramètres de fixation.

### <a name="settings-serialization"></a>Sérialisation de paramètres
 Lorsque <xref:System.Configuration.LocalFileSettingsProvider> doit enregistrer les paramètres du disque, il effectue les actions suivantes :

1. Utilise la réflexion pour examiner toutes <xref:System.Configuration.ApplicationSettingsBase> les propriétés définies sur <xref:System.Configuration.ApplicationScopedSettingAttribute> <xref:System.Configuration.UserScopedSettingAttribute>votre classe dérivée, trouver celles qui sont appliquées avec l’un ou l’autre ou .

2. Sérialise la propriété sur le disque. Il tente d’abord <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> d’appeler le <xref:System.ComponentModel.TypeConverter> <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> ou sur le type associé . Si cela ne réussit pas, la sérialisation XML est utilisée à la place.

3. Détermine quels paramètres vont dans quels fichiers, selon l’attribut du paramètre.

 Si vous implémentez votre propre <xref:System.Configuration.SettingsSerializeAsAttribute> classe de paramètres, vous pouvez utiliser <xref:System.Configuration.SettingsSerializeAs> le pour marquer un paramètre pour la sérialisation binaire ou personnalisée en utilisant le recensement. Pour plus d’informations sur la création de votre propre classe de paramètres en code, consultez [Guide pratique : Créer des paramètres d'application](how-to-create-application-settings.md).

### <a name="settings-file-locations"></a>Emplacements des fichiers de paramètres
 L’emplacement des fichiers `app`.exe.config et *user*.config varie en fonction de la façon dont l’application est installée. Pour une application basée sur Windows Forms `app`copiée sur l’ordinateur local, .exe.config résidera dans le même répertoire que l’annuaire de base du <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> fichier exécutable principal de l’application, et *l’utilisateur*.config résidera dans l’emplacement spécifié par la propriété. Pour une application installée au moyen de ClickOnce, ces deux fichiers résideront dans l’annuaire des\\données ClickOnce sous %InstallRoot% -Documents et Paramètres*nom d’utilisateur*'Paramètres locaux.

 L’emplacement de stockage de ces fichiers est légèrement différent si un utilisateur a activé des profils d’itinérance, ce qui permet à un utilisateur de définir différents Paramètres Windows et d’application lorsqu’il utilise d’autres ordinateurs dans un domaine. Dans ce cas, les applications ClickOnce et les `app`applications non-ClickOnce auront leurs fichiers .exe.config et\\ *utilisateur*.config stockés sous %InstallRoot% 'Documents et Paramètres*nom d’utilisateur*'Application Data.

 Pour plus d’informations sur le fonctionnement de la fonctionnalité Paramètres d’application avec la nouvelle technologie de déploiement, consultez [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings). Pour plus d’informations sur le répertoire de données ClickOnce, voir [accéder aux données locales et à distance dans clickOnce Applications](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Paramètres d’application et sécurité
 Les paramètres d’application sont conçus pour fonctionner en mode de confiance partielle, un environnement restreint qui est la configuration par défaut pour les applications Windows Forms hébergées sur Internet ou sur un intranet. Aucune autorisation spéciale au-delà de la confiance partielle n’est nécessaire pour utiliser les paramètres d’application avec le fournisseur de paramètres par défaut.

 Lorsque les paramètres d’application sont utilisés `user`dans une application ClickOnce, le fichier .config est stocké dans l’annuaire de données ClickOnce. La taille du fichier `user`.config de l’application ne peut pas dépasser le quota d’annuaire des données fixé par ClickOnce. Pour plus d'informations, consultez [ClickOnce et paramètres d’application](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Fournisseurs de paramètres personnalisés
 Dans l’architecture Paramètres d’application, il y a un couplage lâche entre la classe d’emballage des paramètres d’applications, dérivée de <xref:System.Configuration.ApplicationSettingsBase>, et le fournisseur ou fournisseur de paramètres associés, dérivé de <xref:System.Configuration.SettingsProvider>. Cette association n’est <xref:System.Configuration.SettingsProviderAttribute> définie que par l’application à la classe d’emballage ou à ses propriétés individuelles. Si un fournisseur de paramètres n’est <xref:System.Configuration.LocalFileSettingsProvider>pas explicitement spécifié, le fournisseur par défaut, est utilisé. Par conséquent, cette architecture prend en charge la création et l’utilisation de fournisseurs de paramètres personnalisés.

 Par exemple, supposons que vous souhaitez développer et utiliser `SqlSettingsProvider`, un fournisseur qui stockera toutes les données de paramètres dans une base de données Microsoft SQL Server. Votre <xref:System.Configuration.SettingsProvider>classe dérivée recevrait `Initialize` cette information dans <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>sa méthode comme un paramètre de type . Vous implériez <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> ensuite la méthode pour récupérer <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> vos paramètres dans le magasin de données et pour les enregistrer. Votre fournisseur peut <xref:System.Configuration.SettingsPropertyCollection> utiliser <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> le fourni pour déterminer le nom, le type et la portée de la propriété, ainsi que tous les autres attributs de paramètres définis pour cette propriété.

 Votre fournisseur devra implémenter une propriété et une méthode dont les implémentations peuvent ne pas être évidentes. La <xref:System.Configuration.SettingsProvider.ApplicationName%2A> propriété est une <xref:System.Configuration.SettingsProvider>propriété abstraite de ; vous devriez le programmer pour retourner ce qui suit :

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Votre classe dérivée doit également implémenter une méthode `Initialize` qui n’accepte aucun argument et ne retourne aucune valeur. Cette méthode n’est pas définie par <xref:System.Configuration.SettingsProvider>.

 Enfin, vous <xref:System.Configuration.IApplicationSettingsProvider> implémentez votre fournisseur pour fournir une prise en charge des paramètres rafraîchissants, le retour des paramètres à leurs défauts et la mise à niveau des paramètres d’une version d’application à l’autre.

 Une fois que vous avez implémenté et compilé votre fournisseur, vous devez demander à votre classe de paramètres d’utiliser ce fournisseur au lieu de la valeur par défaut. Vous accomplissez <xref:System.Configuration.SettingsProviderAttribute>cela à travers le . S’il est appliqué à une classe de paramètres entier, le fournisseur est utilisé pour chaque paramètre que la classe définit; si elle est appliquée à des paramètres individuels, l’architecture Paramètres d’application utilise ce fournisseur pour ces paramètres seulement, et utilise <xref:System.Configuration.LocalFileSettingsProvider> pour le reste. L’exemple de code suivant montre comment indiquer à la classe de paramètres d’utiliser votre fournisseur personnalisé.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Un fournisseur peut être appelé à partir de plusieurs threads simultanément, mais il écrira toujours au même emplacement de stockage. Par conséquent, l’architecture de paramètres d’application n’instanciera jamais qu’une seule instance de votre classe de fournisseur.

> [!IMPORTANT]
> Vous devez vous assurer que votre fournisseur est thread-safe et autorise un seul thread à la fois à écrire dans les fichiers de configuration.

 Votre fournisseur n’a pas besoin de prendre <xref:System.Configuration?displayProperty=nameWithType> en charge tous les paramètres <xref:System.Configuration.ApplicationScopedSettingAttribute> définis dans l’espace de nom, mais il doit à un minimum de soutien et <xref:System.Configuration.UserScopedSettingAttribute>, et doit également prendre en charge <xref:System.Configuration.DefaultSettingValueAttribute>. Pour les attributs qu’il ne prend pas en charge, votre fournisseur doit simplement échouer sans notification. Il ne doit pas lever une exception. Toutefois, si la classe de paramètres utilise une <xref:System.Configuration.ApplicationScopedSettingAttribute> combinaison <xref:System.Configuration.UserScopedSettingAttribute> d’attributs invalides, par exemple — comme l’application et le même paramètre — votre fournisseur devrait faire exception et cesser de fonctionner.

## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Vue d’ensemble des paramètres d’application](application-settings-overview.md)
- [Paramètres d'application pour les contrôles personnalisés](application-settings-for-custom-controls.md)
- [Paramètres ClickOnce et Application](/visualstudio/deployment/clickonce-and-application-settings)
- [Schéma des paramètres d’application](../../configure-apps/file-schema/application-settings-schema.md)
