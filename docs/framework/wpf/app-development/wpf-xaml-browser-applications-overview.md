---
title: Vue d’ensemble des applications du navigateur XAML
description: Découvrez comment les applications de navigateur XAML combinent les fonctionnalités des applications Web et des applications clientes riches dans le Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 3395445dd5639e25f62aeef09d070e326704ed40
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617910"
---
# <a name="wpf-xaml-browser-applications-overview"></a>Vue d'ensemble des applications de navigateur XAML
<a name="introduction"></a>Les applications de navigateur XAML (XBAP) associent les fonctionnalités des applications Web et des applications clientes riches. À l’instar des applications Web, les applications XBAP peuvent être déployées sur un serveur web et démarrées à partir d’Internet Explorer ou de Firefox. Comme les applications clientes riches, les XBAP peuvent tirer parti des fonctionnalités de WPF. Le développement d’applications XBAP est également semblable au développement d’applications clientes complètes. Cette rubrique fournit une présentation simple et détaillée du développement XBAP et décrit les différences de développement entre les applications XBAP et les applications clientes complètes standard.

 Cette rubrique contient les sections suivantes :

- [Création d’une nouvelle application de navigateur XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)

- [Déploiement d’une application XBAP](#deploying_a_xbap)

- [Communication avec la page web hôte](#communicating_with_the_host_web_page)

- [Considérations relatives à la sécurité des applications XBAP](#xbap_security_considerations)

- [Considérations relatives au temps de démarrage des applications XPAB](#xbap_start_time_performance_considerations)

<a name="creating_a_new_xaml_browser_application_xbap"></a>
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Création d’une nouvelle application de navigateur XAML (XBAP)
 La façon la plus simple de créer un nouveau projet XBAP est avec Visual Studio. Lorsque vous créez un nouveau projet, sélectionnez **Application de navigateur WPF** dans la liste des modèles. Pour plus d’informations, consultez [Guide pratique pour créer un projet d’application de navigateur WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).

 Lorsque vous exécutez le projet XBAP, celui-ci s’ouvre dans une fenêtre de navigateur et non dans une fenêtre indépendante. Quand vous déboguez l’application XBAP à partir de Visual Studio, l’application s’exécute avec l’autorisation de zone Internet et lèvera donc des exceptions de sécurité si ces autorisations sont dépassées. Pour plus d’informations, voir [Sécurité](../security-wpf.md) et [Sécurité de confiance partielle de WPF](../wpf-partial-trust-security.md).

> [!NOTE]
> Si vous ne développez pas avec Visual Studio ou souhaitez en savoir plus sur les fichiers projet, consultez [génération d’une application WPF](building-a-wpf-application-wpf.md).

<a name="deploying_a_xbap"></a>
## <a name="deploying-an-xbap"></a>Déploiement d’une application XBAP
 Lorsque vous générez une application XBAP, la sortie inclut les trois fichiers suivants :

|Fichier|Description|
|----------|-----------------|
|Fichier exécutable (.exe)|Ce fichier contient le code compilé et porte l’extension .exe.|
|Fichier manifeste d’application (.manifest)|Ce fichier contient les métadonnées associées à l’application et porte l’extension .manifest.|
|Fichier manifeste de déploiement (.xbap)|Ce fichier contient les informations utilisées par ClickOnce pour déployer l’application et l’extension. xbap.|

 Vous déployez des applications XBAP sur un serveur Web, par exemple Microsoft Internet Information Services (IIS) 5,0 ou versions ultérieures. Vous n’avez pas besoin d’installer le .NET Framework sur le serveur Web, mais vous devez enregistrer les types MIME (Multipurpose Internet Mail Extensions) WPF et les extensions de nom de fichier. Pour plus d’informations, consultez l’article [Configurer IIS 5.0 et IIS 6.0 pour déployer des applications WPF](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).

 Pour préparer votre application XBAP au déploiement, copiez le fichier .exe et les manifestes associés sur le serveur web. Créez une page HTML qui contient un lien hypertexte pour ouvrir le manifeste de déploiement, c’est-à-dire le fichier qui porte l’extension .xbap. Quand l’utilisateur clique sur le lien vers le fichier. XBAP, ClickOnce gère automatiquement les mécanismes de téléchargement et de démarrage de l’application. L’exemple de code suivant montre une page HTML qui contient un lien hypertexte vers une application XBAP.

```html
<html>
    <head></head>
    <body>
        <a href="XbapEx.xbap">Click this link to launch the application</a>
    </body>
</html>
```

 Vous pouvez également héberger une application XBAP dans le cadre d’une page web. Créez une page web contenant un ou plusieurs cadres. Définissez le fichier manifeste de déploiement comme propriété source d’un cadre. Si vous souhaitez utiliser le mécanisme intégré pour la communication entre la page web hôte et l’application XBAP, vous devez héberger l’application dans un cadre. L’exemple de code suivant montre une page HTML contenant deux cadres et pour laquelle une application XBAP est définie comme source du second cadre.

```html
<html>
    <head>
        <title>A page with frames</title>
    </head>
    <frameset cols="50%,50%">
        <frame src="introduction.htm">
        <frame src="XbapEx.xbap">
    </frameset>
</html>
```

### <a name="clearing-cached-xbaps"></a>Suppression des applications XBAP mises en cache
 Il peut arriver qu’après avoir régénéré et démarré votre application XBAP, une version antérieure de l’application XBAP soit restée ouverte. Cela peut par exemple se produire lorsque votre numéro de version d’assembly XBAP est statique et que vous démarrez l’application XBAP à partir de la ligne de commande. Dans ce cas, étant donné que la version mise en cache (version de l’application démarrée précédemment) et la nouvelle version portent le même numéro de version, la nouvelle version de l’application XBAP n’est pas téléchargée. C’est donc la version mise en cache qui est chargée.

 Dans ce cas, vous pouvez supprimer la version mise en cache à l’aide de la commande **mage** (installée avec Visual Studio ou le SDK Windows) à l’invite de commandes. La commande suivante efface le cache d’application.

 ```console
 Mage.exe -cc
 ```

 Cette commande permet de s’assurer que la dernière version de votre application XBAP est démarrée. Quand vous déboguez votre application dans Visual Studio, vous devez démarrer la dernière version de votre application XBAP. En général, vous devez mettre à jour votre numéro de version de déploiement à chaque version. Pour plus d’informations sur Mage, consultez l’article [Mage.exe (outil Manifest Generation and Editing)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).

<a name="communicating_with_the_host_web_page"></a>
## <a name="communicating-with-the-host-web-page"></a>Communication avec la page web hôte
 Lorsque l’application est hébergée dans un cadre HTML, vous pouvez communiquer avec la page web qui contient l’application XBAP. Pour ce faire, récupérez la <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> propriété de <xref:System.Windows.Interop.BrowserInteropHelper> . Cette propriété renvoie un objet de script qui représente la fenêtre HTML. Vous pouvez consulter les propriétés, méthodes et événements sur [l’objet de fenêtre](https://developer.mozilla.org/en-US/docs/Web/API/Window) en utilisant la syntaxe de point normale. Vous pouvez également accéder aux méthodes de script et aux variables globales. L’exemple suivant montre comment récupérer l’objet de script et fermer le navigateur.

 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]

### <a name="debugging-xbaps-that-use-hostscript"></a>Débogage des applications XBAP qui utilisent HostScript
 Si votre application XBAP utilise l' <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> objet pour communiquer avec la fenêtre HTML, vous devez spécifier deux paramètres pour exécuter et déboguer l’application dans Visual Studio. L’application doit avoir accès à son site d’origine et vous devez démarrer l’application avec la page HTML qui contient l’application XBAP. Les étapes suivantes décrivent comment vérifier ces deux paramètres :

1. Dans Visual Studio, ouvrez les propriétés du projet.

2. Sous l’onglet **Sécurité**, cliquez sur **Avancé**.

     La boîte de dialogue Paramètres de sécurité avancés s'affiche.

3. Assurez-vous que la case **Autoriser l’application à accéder à son site d’origine** est cochée, puis cliquez sur **OK**.

4. Dans l’onglet **Déboguer**, sélectionnez l’option **Démarrer le navigateur avec l’URL** et spécifiez l’URL de la page HTML qui contient l’application XBAP.

5. Dans Internet Explorer, cliquez sur le bouton **Outils**, puis sélectionnez **Options Internet**.

     La boîte de dialogue Options Internet apparaît.

6. Cliquez sur l'onglet **Avancé**.

7. Dans la liste des **paramètres** sous **Sécurité**, cochez la case **Autoriser l’exécution du contenu actif dans les fichiers de mon ordinateur**.

8. Cliquez sur **OK**.

     Les modifications prendront effet après le redémarrage d’Internet Explorer.

> [!CAUTION]
> Activer le contenu actif dans Internet Explorer peut représenter un risque pour votre ordinateur. Si vous ne souhaitez pas modifier vos paramètres de sécurité Internet Explorer, vous pouvez lancer la page HTML à partir d’un serveur et attacher le débogueur Visual Studio au processus.

<a name="xbap_security_considerations"></a>
## <a name="xbap-security-considerations"></a>Considérations relatives à la sécurité des applications XBAP
 Les applications XBAP s’exécutent généralement dans un sandbox de sécurité de confiance partielle qui est limité au jeu d’autorisations de la zone Internet. Par conséquent, votre implémentation doit prendre en charge le sous-ensemble d’éléments WPF pris en charge dans la zone Internet ou vous devez élever les autorisations de votre application. Pour plus d’informations, consultez [Sécurité](../security-wpf.md).

 Quand vous utilisez un <xref:System.Windows.Controls.WebBrowser> contrôle dans votre application, WPF instancie en interne le contrôle ActiveX WebBrowser natif. Lorsque votre application est exécutée en tant qu’application XBAP de confiance partielle dans Internet Explorer, le contrôle ActiveX s’exécute dans un thread dédié du processus Internet Explorer. Cela signifie que les limitations suivantes s’appliquent :

- Le <xref:System.Windows.Controls.WebBrowser> contrôle doit fournir un comportement similaire au navigateur hôte, y compris des restrictions de sécurité. Certaines de ces restrictions de sécurité peuvent être gérées via les paramètres de sécurité d’Internet Explorer. Pour plus d’informations, consultez [Sécurité](../security-wpf.md).

- Une exception est générée lorsqu’une application XBAP est chargée sur plusieurs domaines dans une page HTML.

- L’entrée se trouve sur un thread distinct du WPF <xref:System.Windows.Controls.WebBrowser> , de sorte que l’entrée au clavier ne peut pas être interceptée et que l’état de l’IME n’est pas partagé.

- Comme le contrôle ActiveX est en cours d’exécution sur un autre thread, le temps ou l’ordre de navigation peut différer. Par exemple, la navigation vers une page n’est pas toujours annulée lors du démarrage d’une autre requête de navigation.

- La communication avec un contrôle ActiveX personnalisé peut être difficile puisque l’application WPF s’exécute dans un thread distinct.

- <xref:System.Windows.Interop.HwndHost.MessageHook>n’est pas déclenché, car <xref:System.Windows.Interop.HwndHost> ne peut pas sous-traiter une fenêtre qui s’exécute dans un autre thread ou processus.

### <a name="creating-a-full-trust-xbap"></a>Création d’une application XBAP de confiance totale
 Si votre application XBAP requiert une confiance totale, vous pouvez modifier votre projet pour activer cette autorisation. Les étapes suivantes décrivent comment activer la confiance totale :

1. Dans Visual Studio, ouvrez les propriétés du projet.

2. Dans l’onglet **Sécurité**, sélectionnez l’option **This is a full trust application** (Ceci est une application de confiance totale).

 Ce paramètre apporte les modifications suivantes :

- Dans le fichier projet, la valeur de l’élément `<TargetZone>` devient `Custom`.

- Dans le manifeste de l’application (App. manifest), un `Unrestricted="true"` attribut est ajouté à l' <xref:System.Security.PermissionSet> élément.

    ```xml
    <PermissionSet class="System.Security.PermissionSet"
                   version="1"
                   ID="Custom"
                   SameSite="site"
                   Unrestricted="true" />
    ```

### <a name="deploying-a-full-trust-xbap"></a>Déploiement d’une application XBAP de confiance totale
 Lorsque vous déployez une application XBAP de confiance totale qui ne suit pas le modèle de déploiement approuvé ClickOnce, le comportement fourni lorsque l’utilisateur exécute l’application dépend de la zone de sécurité. Dans certains cas, l’utilisateur reçoit un avertissement quand il tente de l’installer. Il peut choisir de continuer ou d’annuler l’installation. Le tableau suivant décrit le comportement de l’application pour chaque zone de sécurité et ce que vous devez faire pour que l’application reçoive la confiance totale.

|Zone de sécurité|Comportement|Obtention de la confiance totale|
|-------------------|--------------|------------------------|
|Ordinateur local|Confiance totale automatique|Aucune action n'est nécessaire.|
|Intranet et sites de confiance|Invite pour la confiance totale|Signez l’application XBAP avec un certificat afin que l’utilisateur consulte la source dans l’invite.|
|Internet|Échec avec "Confiance non accordée"|Signez l’application XBAP avec un certificat.|

> [!NOTE]
> Le comportement décrit dans le tableau précédent concerne les applications XBAP de confiance totale qui ne suivent pas le modèle de déploiement approuvé ClickOnce.

 Il est recommandé d’utiliser le modèle de déploiement approuvé ClickOnce pour déployer une application XBAP de confiance totale. Ce modèle permet d’accorder automatiquement une confiance totale à votre application XBAP, quelle que soit la zone de sécurité, afin que l’utilisateur ne reçoive aucune invite. Dans le cadre de ce modèle, vous devez signer votre application avec un certificat d’un éditeur approuvé. Pour plus d’informations, consultez les articles [Vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview) et [Présentation de la signature de code](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537361(v=vs.85)).

<a name="xbap_start_time_performance_considerations"></a>
## <a name="xbap-start-time-performance-considerations"></a>Considérations relatives au temps de démarrage des applications XPAB
 Un facteur important de performance d’une application XBAP est son temps de démarrage. Si une application XBAP est la première application WPF à être chargée, le *démarrage à froid* prend au moins dix secondes. Cela s’explique par le fait que la page de progression est affichée par WPF, et que CLR et WPF doivent être démarrés à froid pour afficher l’application.

 À compter de .NET Framework 3,5 SP1, l’heure de démarrage à froid de XBAP est atténuée en affichant une page de progression non gérée au début du cycle de déploiement. La page de progression s’affiche quasiment immédiatement après le démarrage de l’application, car elle apparaît via le code d’hébergement natif au format HTML.

 En outre, la concurrence améliorée de la séquence de téléchargement ClickOnce améliore le temps de démarrage jusqu’à dix pour cent. Une fois que ClickOnce a téléchargé et validé les manifestes, le téléchargement de l’application démarre et la barre de progression commence à se mettre à jour.

## <a name="see-also"></a>Voir aussi

- [Configurer Visual Studio pour déboguer une application de navigateur XAML et appeler un service web](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [Déploiement d’une application WPF](deploying-a-wpf-application-wpf.md)
