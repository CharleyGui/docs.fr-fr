---
title: Comment configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures
ms.date: 03/30/2017
helpviewer_keywords:
- configuring apps to support .NET Framework
- .NET Framework, configuring apps
ms.assetid: 63c6b9a8-0088-4077-9aa3-521ab7290f79
ms.openlocfilehash: 30fb1da8d758b0e8996b4fcdebbb7fbf545a46c1
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228759"
---
# <a name="how-to-configure-an-app-to-support-net-framework-4-or-later-versions"></a>Comment : Configurer une application pour prendre en charge .NET Framework 4 ou des versions ultérieures

Toutes les applications qui hébergent le Common Langage Runtime (CLR) doivent démarrer, ou *activer*, le CLR afin d'exécuter le code managé. En général, une application .NET Framework s'exécute sur la version du CLR pour laquelle elle a été générée, mais vous pouvez modifier ce comportement pour les applications de bureau en utilisant un fichier de configuration d'application (parfois appelé fichier app.config). Toutefois, vous ne pouvez pas modifier le comportement d'activation par défaut des applications Windows Store ou des applications Windows Phone en utilisant un fichier de configuration d'application. Cet article explique comment permettre à votre application de bureau de s’exécuter sur une autre version du .NET Framework et fournit un exemple de la façon de cibler les versions 4 ou ultérieures.

 La version du .NET Framework sur laquelle une application s'exécute est déterminée dans l'ordre suivant :

- Fichier de configuration

     Si le fichier [ \<](../configure-apps/file-schema/startup/supportedruntime-element.md) de configuration d’application inclut les entrées de>prises de position prises en charge qui spécifient une ou plusieurs versions cadres .NET, et que l’une de ces versions est présente sur l’ordinateur de l’utilisateur, l’application s’exécute sur cette version. Le fichier [ \<](../configure-apps/file-schema/startup/supportedruntime-element.md) de configuration lit les entrées supportRuntime>dans l’ordre où elles sont répertoriées, et utilise la première version cadre .NET répertoriée qui est présente sur l’ordinateur de l’utilisateur. (Utilisez [ \<l’élément> deruntime requis](../configure-apps/file-schema/startup/requiredruntime-element.md) pour la version 1.0.)

- Version compilée

     S'il n'existe aucun fichier de configuration, mais si la version du .NET Framework pour laquelle l'application a été générée est présente sur l'ordinateur de l'utilisateur, l'application s'exécute sur cette version.

- Dernière version installée

     Si la version du cadre .NET sur lequel l’application a été construite n’est pas présente et qu’un fichier de configuration ne spécifie pas une version dans un [ \<élément> supportRuntime,](../configure-apps/file-schema/startup/supportedruntime-element.md)l’application tente de s’exécuter sur la dernière version du cadre .NET qui est présent sur l’ordinateur de l’utilisateur.

     Toutefois, les applications .NET Framework 1.0, 1.1, 2.0, 3.0 et 3.5 ne s'exécutent pas automatiquement sur .NET Framework 4 ou version ultérieure et, dans certains cas, l'utilisateur peut obtenir un message d'erreur et être invité à installer .NET Framework 3.5. Le comportement d'activation peut également dépendre du système d'exploitation de l'utilisateur, car les différentes versions du système Windows incluent différentes versions du .NET Framework. Si votre application prend en charge .NET Framework 3.5 et 4, ou version ultérieure, nous vous recommandons de l'indiquer à l'aide de plusieurs entrées dans le fichier de configuration, afin d'éviter des erreurs d'initialisation du .NET Framework. Pour plus d’informations, consultez [Versions et dépendances](versions-and-dependencies.md).

 Vous pouvez également configurer vos applications .NET Framework 3.5 pour qu’elles s’exécutent sur .NET Framework version 4 ou ultérieur, même sur les ordinateurs où .NET Framework 3.5 est installé, afin de tirer parti des améliorations des performances dans les versions 4 et ultérieures.

> [!IMPORTANT]
> Nous vous recommandons de toujours tester votre application sur chaque version du .NET Framework que vous prenez en charge. Pour plus d'informations sur la mise à niveau d'une application de manière à prendre en charge des versions ultérieures du .NET Framework, consultez [Compatibilité de versions](version-compatibility.md).

 Pour plus d'informations sur la modification d'applications .NET Framework 1.0 et 1.1 pour prendre en charge Windows 7 et Windows 8, consultez [Migration à partir du .NET Framework 1.1](migrating-from-the-net-framework-1-1.md).

## <a name="to-configure-your-app-to-run-on-the-net-framework-4-or-later-versions"></a>Pour configurer votre application afin qu’elle s’exécute sur .NET Framework version 4 ou ultérieur

1. Ajoutez ou recherchez le fichier de configuration pour le projet .NET Framework. Le fichier de configuration d'une application se trouve dans le même répertoire et porte le même nom que l'application, mais il possède une extension .config. Par exemple, à une application nommée MyExecutable.exe correspond le fichier de configuration de l'application nommé MyExecutable.exe.config.

     Pour ajouter un fichier de configuration, dans la barre de menus de Visual Studio, choisissez **Projet**, **Ajouter un nouvel élément**. Choisissez **Général** dans le volet gauche, puis choisissez **Fichier de configuration**. Nommez l’application de fichier de *configurationName*.exe.config. Ces choix de menu ne sont pas disponibles pour les projets d’applications Windows Store ou Windows phone, car vous ne pouvez pas modifier la politique d’activation sur ces plates-formes.

2. Ajoutez l’élément [ \<de>supportRuntime](../configure-apps/file-schema/startup/supportedruntime-element.md) comme suit au fichier de configuration d’application :

    ```xml
    <configuration>
      <startup>
        <supportedRuntime version="version"/>
      </startup>
    </configuration>
    ```

     où la * \<version>* spécifie la version CLR qui s’aligne avec la version cadre .NET que votre application prend en charge. Utilisez les chaînes suivantes :

    - .NET Framework 1.0 : "v1.0.3705"

    - .NET Framework 1.1 : "v1.1.4322"

    - .NET Framework 2.0, 3.0 et 3.5 : "v2.0.50727"

    - .NET Framework version 4 et ultérieur : "v4.0"

     Vous pouvez ajouter plusieurs [ \<éléments>SupportRuntime,](../configure-apps/file-schema/startup/supportedruntime-element.md) répertoriés par ordre de préférence, pour spécifier la prise en charge de plusieurs versions du cadre .NET.

 Le tableau ci-dessous montre comment les paramètres du fichier de configuration de l'application et les versions du .NET Framework installées sur un ordinateur déterminent la version sur laquelle une application .NET Framework 3.5 s'exécute. Les exemples sont spécifiques à une application .NET Framework 3.5, mais vous pouvez utiliser une logique similaire pour cibler des applications générées à l'aide de versions antérieures du .NET Framework. Notez que le numéro de version de .NET Framework 2.0 (v2.0.50727) est utilisé pour spécifier .NET Framework 3.5 dans le fichier de configuration de l'application.

|Paramètre du fichier app.config|Sur un ordinateur doté de la version 3.5|Sur un ordinateur doté des versions 3.5, 4 ou ultérieures|Sur un ordinateur doté des versions 4 ou ultérieures|
|-|-|-|-|
|None|S'exécute sur 3.5|S'exécute sur 3.5|Affiche un message d'erreur qui invite l'utilisateur à installer la version correcte*|
|`<supportedRuntime version="v2.0.50727"/>`|S'exécute sur 3.5|S'exécute sur 3.5|Affiche un message d'erreur qui invite l'utilisateur à installer la version correcte*|
|`<supportedRuntime version="v2.0.50727"/>` <br /> `<supportedRuntime version="v4.0"/>`|S'exécute sur 3.5|S'exécute sur 3.5|S’exécute sur la version 4 ou ultérieur|
|`<supportedRuntime version="v4.0"/>` <br /> `<supportedRuntime version="v2.0.50727"/>`|S'exécute sur 3.5|S’exécute sur la version 4 ou ultérieur|S’exécute sur la version 4 ou ultérieur|
|`<supportedRuntime version="v4.0"/>`|Affiche un message d'erreur qui invite l'utilisateur à installer la version correcte*|S’exécute sur la version 4 ou ultérieur|S’exécute sur la version 4 ou ultérieur|

 \*Pour plus d'informations sur ce message d'erreur et les moyens de l'éviter, consultez [Erreurs d'initialisation de .NET Framework : gérer l'expérience utilisateur](../deployment/initialization-errors-managing-the-user-experience.md).

## <a name="see-also"></a>Voir aussi

- [Migration à partir du .NET Framework 1.1](migrating-from-the-net-framework-1-1.md)
- [Migration Guide](index.md)
