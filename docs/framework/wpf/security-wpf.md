---
title: Sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- XAML files [WPF], sandbox behavior
- browser-hosted application security [WPF]
- application security [WPF]
- navigation security [WPF]
- loose XAML files [WPF], sandbox behavior
- WPF security [WPF]
- WebBrowser control [WPF], security
- feature controls [WPF], security
- XBAP security [WPF]
- Internet Explorer security settings [WPF]
ms.assetid: ee1baea0-3611-4e36-9ad6-fcd5205376fb
ms.openlocfilehash: a49634fd955b0dc1f4cac5c785d49c24d16bbc60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868042"
---
# <a name="security-wpf"></a>Sécurité (WPF)
<a name="introduction"></a>Lors du développement d’applications autonomes et hébergées par un navigateur Windows Presentation Foundation (WPF), vous devez prendre en compte le modèle de sécurité. Les applications autonomes WPF s’exécutent avec des autorisations illimitées (jeu d’autorisations**FullTrust** de l’autorité de certification), qu’elles soient déployées à l’aide de Windows Installer (. msi), xcopy ou ClickOnce. Le déploiement d’applications WPF autonomes de confiance partielle avec ClickOnce n’est pas pris en charge. Toutefois, une application hôte de confiance totale peut créer un <xref:System.AppDomain> de confiance partielle à l’aide du modèle de complément .NET Framework. Pour plus d’informations, consultez [vue d’ensemble des compléments WPF](./app-development/wpf-add-ins-overview.md).  
  
 Les applications hébergées par le navigateur WPF sont hébergées par Windows Internet Explorer ou Firefox et peuvent être des applications de navigateur XAML (XBAP) ou des documents [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] libres. pour plus d’informations, consultez [vue d’ensemble des applications de navigateur XAML WPF](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 Les applications hébergées par le navigateur WPF s’exécutent dans un bac à sable (sandbox) de sécurité de confiance partielle, qui est limité au jeu d’autorisations de la zone**Internet** de l’autorité de certification par défaut. Cela isole efficacement les applications hébergées par le navigateur WPF de l’ordinateur client de la même façon que les applications Web typiques sont isolées. Une application XBAP peut élever des privilèges jusqu’à la confiance totale, selon la zone de sécurité de l’URL de déploiement et la configuration de sécurité du client. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](wpf-partial-trust-security.md).  
  
 Cette rubrique décrit le modèle de sécurité pour les applications autonomes et hébergées par un navigateur Windows Presentation Foundation (WPF).  
  
 Cette rubrique contient les sections suivantes :  
  
- [Sécurité de la navigation](#SafeTopLevelNavigation)  
  
- [Paramètres de sécurité des logiciels de navigation web](#InternetExplorerSecuritySettings)  
  
- [Contrôle WebBrowser et contrôles de fonctionnalités](#webbrowser_control_and_feature_controls)  
  
- [Désactivation des assemblys APTCA pour les applications clientes partiellement fiables](#APTCA)  
  
- [Comportement de bac à sable pour les fichiers en XAML libre](#LooseContentSandboxing)  
  
- [Ressources pour le développement d’applications WPF promouvant la sécurité](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>   
## <a name="safe-navigation"></a>Sécurité de la navigation  
 Pour les applications XBAP, WPF distingue deux types de navigation : application et navigateur.  
  
 La *navigation dans une application* est la navigation entre les éléments de contenu dans une application hébergée par un navigateur. La *navigation dans un navigateur* est la navigation qui modifie l’URL de contenu et d’emplacement d’un navigateur lui-même. La relation entre la navigation dans l’application (en général XAML) et la navigation dans le navigateur (en général HTML) est indiquée dans l’illustration suivante :
  
 ![Relation entre la navigation dans l’application et la navigation dans le navigateur.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Le type de contenu considéré comme sécurisé pour une application XBAP à atteindre est principalement déterminé par l’utilisation de la navigation dans l’application ou de la navigation dans le navigateur.  
  
<a name="Application_Navigation_Security"></a>   
### <a name="application-navigation-security"></a>Sécurité de la navigation dans une application  
 La navigation dans les applications est considérée comme sécurisée si elle peut être identifiée à l’aide d’un URI à en-tête pack, qui prend en charge quatre types de contenu :  
  
|Type de contenu|Description|Exemple d’URI|  
|------------------|-----------------|-----------------|  
|Ressource|Fichiers ajoutés à un projet avec un type de build **ressource**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Contenu|Fichiers ajoutés à un projet avec un type de build de **contenu**.|`pack://application:,,,/MyContentFile.xaml`|  
|Site d’origine|Fichiers ajoutés à un projet avec un type de build **None**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Code de l’application|Ressources XAML avec un code-behind compilé.<br /><br /> \- ou -<br /><br /> Fichiers XAML qui sont ajoutés à un projet avec un type de build de **page**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Pour plus d’informations sur les fichiers de données d’application et les URI à en-tête pack, consultez [fichiers de ressources, de contenu et de données d’une application WPF](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Les fichiers ayant ces types de contenu sont accessibles par l’utilisateur et par programme :  
  
- **Navigation utilisateur**. L’utilisateur navigue en cliquant sur un élément <xref:System.Windows.Documents.Hyperlink>.  
  
- **Navigation par programme**. L’application navigue sans impliquer l’utilisateur, par exemple, en définissant la propriété <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>.  
  
<a name="Browser_Navigation_Security"></a>   
### <a name="browser-navigation-security"></a>Sécurité de la navigation dans un navigateur  
 La navigation dans un navigateur est considérée comme sûre uniquement si les conditions suivantes sont respectées :  
  
- **Navigation utilisateur**. L’utilisateur navigue en cliquant sur un élément <xref:System.Windows.Documents.Hyperlink> qui se trouve dans le <xref:System.Windows.Navigation.NavigationWindow>principal, et non dans un <xref:System.Windows.Controls.Frame>imbriqué.  
  
- **Zone**. Le contenu cible de la navigation se trouve sur Internet ou sur l’intranet local.  
  
- **Protocole**. Le protocole utilisé est **http**, **https**, **file**ou **mailto**.  
  
 Si une application XBAP tente d’accéder au contenu d’une manière qui n’est pas conforme à ces conditions, une <xref:System.Security.SecurityException> est levée.  
  
<a name="InternetExplorerSecuritySettings"></a>   
## <a name="web-browsing-software-security-settings"></a>Paramètres de sécurité des logiciels de navigation web  
 Les paramètres de sécurité de votre ordinateur déterminent l’accès accordé à n’importe quel logiciel de navigation web. Le logiciel de navigation Web inclut tout composant ou application qui utilise les API [WinInet](/windows/win32/wininet/portal) ou [urlmon](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) , y compris Internet Explorer et PresentationHost. exe.  
  
 Internet Explorer fournit un mécanisme permettant de configurer les fonctionnalités autorisées à être exécutées par ou à partir d’Internet Explorer, y compris les éléments suivants :  
  
- Composants dépendants de la .NET Framework  
  
- Plug-ins et contrôles ActiveX  
  
- Téléchargements  
  
- Scripts  
  
- Authentification des utilisateurs  
  
 La collection de fonctionnalités qui peuvent être sécurisées de cette manière est configurée par zone pour les zones **Internet**, **Intranet**, **sites de confiance**et **sites sensibles** . Les étapes suivantes décrivent comment configurer vos paramètres de sécurité :  
  
1. Ouvrez le **Panneau de configuration**.  
  
2. Cliquez sur **réseau et Internet** , puis sur **Options Internet**.  
  
     La boîte de dialogue Options Internet apparaît.  
  
3. Sous l’onglet **sécurité** , sélectionnez la zone pour laquelle configurer les paramètres de sécurité.  
  
4. Cliquez sur le bouton **personnaliser le niveau** .  
  
     La boîte de dialogue **paramètres de sécurité** s’affiche et vous pouvez configurer les paramètres de sécurité de la zone sélectionnée.  
  
     ![Capture d’écran montrant la boîte de dialogue Paramètres de sécurité.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Vous pouvez également accéder à la boîte de dialogue Options Internet à partir d’Internet Explorer. Cliquez sur **Outils** , puis sur **Options Internet**.  
  
 À compter de Windows Internet Explorer 7, les paramètres de sécurité suivants, spécifiquement pour .NET Framework, sont inclus :  
  
- **XAML libre**. Contrôle si Internet Explorer peut accéder aux fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ou les rendre libres. (Options Activer, Désactiver et Demander).  
  
- **Applications du navigateur XAML**. Contrôle si Internet Explorer peut accéder aux applications XBAP et les exécuter. (Options Activer, Désactiver et Demander).  
  
 Par défaut, ces paramètres sont tous activés pour les zones **Internet**, **Intranet local**et **sites de confiance** , et sont désactivés pour la zone **sites sensibles** .  
  
<a name="Security_Settings_for_IE6_and_Below"></a>   
### <a name="security-related-wpf-registry-settings"></a>Paramètres du Registre WPF relatifs à la sécurité  
 Outre les paramètres de sécurité disponibles avec les options Internet, les valeurs de Registre suivantes sont disponibles pour le blocage sélectif de certaines fonctionnalités WPF liées à la sécurité. Les valeurs sont définies sous la clé suivante :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Le tableau ci-dessous répertorie les valeurs qui peuvent être définies.  
  
|Nom de valeur|Type valeur|Valeur des données|  
|----------------|----------------|----------------|  
|XBAPDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
|LooseXamlDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
|WebBrowserDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
|MediaAudioDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
|MediaImageDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
|MediaVideoDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
|ScriptInteropDisallow|REG_DWORD|1 pour interdire ; 0 pour autoriser.|  
  
<a name="webbrowser_control_and_feature_controls"></a>   
## <a name="webbrowser-control-and-feature-controls"></a>Contrôle WebBrowser et contrôles de fonctionnalités  
 Le contrôle de <xref:System.Windows.Controls.WebBrowser> WPF peut être utilisé pour héberger du contenu Web. Le contrôle de <xref:System.Windows.Controls.WebBrowser> WPF encapsule le contrôle ActiveX WebBrowser sous-jacent. WPF offre une prise en charge de la sécurisation de votre application lorsque vous utilisez le contrôle de <xref:System.Windows.Controls.WebBrowser> WPF pour héberger du contenu Web non fiable. Toutefois, certaines fonctionnalités de sécurité doivent être appliquées directement par les applications à l’aide du contrôle <xref:System.Windows.Controls.WebBrowser>. Pour plus d’informations sur le contrôle ActiveX WebBrowser, consultez [vues d’ensemble et didacticiels du contrôle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).  
  
> [!NOTE]
> Cette section s’applique également au contrôle <xref:System.Windows.Controls.Frame>, car il utilise le <xref:System.Windows.Controls.WebBrowser> pour accéder au contenu HTML.  
  
 Si le contrôle de <xref:System.Windows.Controls.WebBrowser> WPF est utilisé pour héberger du contenu Web non approuvé, votre application doit utiliser une <xref:System.AppDomain> de confiance partielle pour aider à isoler le code de votre application du code de script HTML potentiellement malveillant. Cela est particulièrement vrai si votre application interagit avec le script hébergé à l’aide de la méthode <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> et de la propriété <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A>. Pour plus d’informations, consultez [vue d’ensemble des compléments WPF](./app-development/wpf-add-ins-overview.md).  
  
 Si votre application utilise le contrôle de <xref:System.Windows.Controls.WebBrowser> WPF, une autre façon d’augmenter la sécurité et d’atténuer les attaques consiste à activer les contrôles de fonctionnalités d’Internet Explorer. Les contrôles de fonctionnalités sont des ajouts à Internet Explorer qui permettent aux administrateurs et aux développeurs de configurer des fonctionnalités d’Internet Explorer et des applications qui hébergent le contrôle ActiveX WebBrowser, que le contrôle <xref:System.Windows.Controls.WebBrowser> WPF encapsule. Les contrôles de fonctionnalités peuvent être configurés à l’aide de la fonction [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) ou en modifiant les valeurs dans le registre. Pour plus d’informations sur les contrôles de fonctionnalités, consultez Présentation des contrôles [de fonctionnalités](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) et des [contrôles de fonctionnalités Internet](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).  
  
 Si vous développez une application WPF autonome qui utilise le contrôle de <xref:System.Windows.Controls.WebBrowser> WPF, WPF active automatiquement les contrôles de fonctionnalités suivants pour votre application.  
  
|Contrôle de fonctionnalité|  
|---------------------|  
|FEATURE_MIME_HANDLING|  
|FEATURE_MIME_SNIFFING|  
|FEATURE_OBJECT_CACHING|  
|FEATURE_SAFE_BINDTOOBJECT|  
|FEATURE_WINDOW_RESTRICTIONS|  
|FEATURE_ZONE_ELEVATION|  
|FEATURE_RESTRICT_FILEDOWNLOAD|  
|FEATURE_RESTRICT_ACTIVEXINSTALL|  
|FEATURE_ADDON_MANAGEMENT|  
|FEATURE_HTTP_USERNAME_PASSWORD_DISABLE|  
|FEATURE_SECURITYBAND|  
|FEATURE_UNC_SAVEDFILECHECK|  
|FEATURE_VALIDATE_NAVIGATE_URL|  
|FEATURE_DISABLE_TELNET_PROTOCOL|  
|FEATURE_WEBOC_POPUPMANAGEMENT|  
|FEATURE_DISABLE_LEGACY_COMPRESSION|  
|FEATURE_SSLUX|  
  
 Étant donné que ces contrôles de fonctionnalités sont activés sans condition, ils peuvent perturber une application de confiance totale. Dans ce cas, s’il n’existe aucun risque de sécurité pour l’application spécifique et le contenu qu’elle héberge, le contrôle de fonctionnalité correspondant peut être désactivé.  
  
 Les contrôles de fonctionnalités sont appliqués par le processus qui instancie l’objet ActiveX WebBrowser. Par conséquent, si vous créez une application autonome qui peut accéder à un contenu non approuvé, vous devez sérieusement envisager d’activer des contrôles de fonctionnalités supplémentaires.  
  
> [!NOTE]
> Cette recommandation est basée sur les recommandations générales sur la sécurité des hôtes MSHTML et SHDOCVW. Pour plus d’informations, consultez [le Forum aux questions sur la sécurité de l’hôte MSHTML : partie I sur II](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) et [le faq sur la sécurité de l’hôte MSHTML : partie II de II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).  
  
 Pour votre fichier exécutable, envisagez d’activer les contrôles de fonctionnalités suivants en définissant la valeur de Registre sur 1.  
  
|Contrôle de fonctionnalité|  
|---------------------|  
|FEATURE_ACTIVEX_REPURPOSEDETECTION|  
|FEATURE_BLOCK_LMZ_IMG|  
|FEATURE_BLOCK_LMZ_OBJECT|  
|FEATURE_BLOCK_LMZ_SCRIPT|  
|FEATURE_RESTRICT_RES_TO_LMZ|  
|FEATURE_RESTRICT_ABOUT_PROTOCOL_IE7|  
|FEATURE_SHOW_APP_PROTOCOL_WARN_DIALOG|  
|FEATURE_LOCALMACHINE_LOCKDOWN|  
|FEATURE_FORCE_ADDR_AND_STATUS|  
|FEATURE_RESTRICTED_ZONE_WHEN_FILE_NOT_FOUND|  
  
 Pour votre fichier exécutable, envisagez de désactiver le contrôle de fonctionnalité suivant en définissant la valeur de Registre sur 0.  
  
|Contrôle de fonctionnalité|  
|---------------------|  
|FEATURE_ENABLE_SCRIPT_PASTE_URLACTION_IF_PROMPT|  
  
 Si vous exécutez une application de navigateur XAML de confiance partielle (XBAP) qui comprend un contrôle de <xref:System.Windows.Controls.WebBrowser> WPF dans Windows Internet Explorer, WPF héberge le contrôle ActiveX WebBrowser dans l’espace d’adressage du processus Internet Explorer. Étant donné que le contrôle ActiveX WebBrowser est hébergé dans le processus Internet Explorer, tous les contrôles de fonctionnalités pour Internet Explorer sont également activés pour le contrôle ActiveX WebBrowser.  
  
 Les applications XBAP exécutées dans Internet Explorer bénéficient également d’un niveau de sécurité supplémentaire par rapport aux applications autonomes normales. Cette sécurité supplémentaire est due au fait qu’Internet Explorer et, par conséquent, le contrôle ActiveX WebBrowser, s’exécute en mode protégé par défaut sur Windows Vista et Windows 7. Pour plus d’informations sur le mode protégé, consultez [présentation et utilisation du mode protégé d’Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).  
  
> [!NOTE]
> Si vous essayez d’exécuter une application XBAP qui comprend un contrôle de <xref:System.Windows.Controls.WebBrowser> WPF dans Firefox, alors que dans la zone Internet, un <xref:System.Security.SecurityException> est levé. conformément à la stratégie de sécurité de WPF.  
  
<a name="APTCA"></a>   
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Désactivation des assemblys APTCA pour les applications clientes partiellement fiables  
 Lorsque des assemblys managés sont installés dans le Global Assembly Cache (GAC), ils deviennent entièrement fiables, car l’utilisateur doit fournir une autorisation explicite pour les installer. Dans la mesure où ils sont entièrement fiables, seules les applications clientes managées entièrement fiables peuvent les utiliser. Pour permettre aux applications de confiance partielle de les utiliser, elles doivent être marquées avec l' <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Seuls les assemblys dont la sécurité d’exécution a été testée pour une confiance partielle doivent être marqués avec cet attribut.  
  
 Toutefois, il est possible pour un assembly APTCA d’exposer une faille de sécurité après son installation dans le GAC. Lorsqu’une faille de sécurité est découverte, les éditeurs d’assembly peuvent produire une mise à jour de sécurité pour résoudre le problème sur les installations existantes et pour assurer une protection vis-à-vis des installations effectuées après la détection du problème. Pour la mise à jour, une option consiste à désinstaller l’assembly, bien que cela risque de bloquer d’autres applications clientes entièrement fiables qui utilisent l’assembly.  
  
 WPF fournit un mécanisme par lequel un assembly APTCA peut être désactivé pour les applications XBAP partiellement fiables sans désinstaller l’assembly APTCA.  
  
 Pour désactiver un assembly APTCA, vous devez créer une clé de Registre spéciale :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Un exemple est fourni ci-après :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Cette clé établit une entrée pour l’assembly APTCA. Vous devez également créer une valeur dans cette clé, qui active ou désactive l’assembly. Voici les détails de la valeur :  
  
- Nom de la valeur : **APTCA_FLAG**.  
  
- Type de valeur : **REG_DWORD**.  
  
- Données de la valeur : **1** à désactiver ; **0** pour activer.  
  
 Si un assembly doit être désactivé pour des applications clientes partiellement fiables, vous pouvez écrire une mise à jour qui crée la clé de Registre et la valeur.  
  
> [!NOTE]
> Les assemblys .NET Framework principaux ne sont pas affectés par leur désactivation de cette manière, car ils sont nécessaires pour que les applications managées s’exécutent. La prise en charge de la désactivation des assemblys APTCA est principalement destinée aux applications tierces.  
  
<a name="LooseContentSandboxing"></a>   
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Comportement de bac à sable pour les fichiers en XAML libre  
 Les fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libres sont des fichiers XAML de balisage qui ne dépendent pas d’un assembly code-behind, d’un gestionnaire d’événements ou d’un assembly spécifique à l’application. En cas de navigation directe entre les fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] distants à partir du navigateur, ils sont chargés dans un bac à sable (sandbox) de sécurité basé sur le jeu d’autorisations de la zone Internet par défaut.  
  
 Toutefois, le comportement de sécurité est différent en cas de navigation dans les fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libres à partir d’un <xref:System.Windows.Navigation.NavigationWindow> ou d’un <xref:System.Windows.Controls.Frame> dans une application autonome.  
  
 Dans les deux cas, le fichier [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libre qui est parcouru hérite des autorisations de son application hôte. Toutefois, ce comportement peut ne pas être souhaitable du point de vue de la sécurité, en particulier si un fichier [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] libre a été produit par une entité qui n’est ni approuvée ni inconnue. Ce type de contenu est connu sous le nom de *contenu externe*, et les <xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow> peuvent être configurés pour l’isoler lors de la navigation. L’isolation est obtenue en affectant à la propriété **à SandboxExternalContent** la valeur true, comme indiqué dans les exemples suivants pour <xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Avec ce paramétrage, le contenu externe sera chargé dans un processus distinct du processus qui héberge l’application. Ce processus, limité au jeu d’autorisations de la zone Internet par défaut, l’isole efficacement de l’application d’hébergement et de l’ordinateur client.  
  
> [!NOTE]
> Même si la navigation pour libérer des fichiers [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] à partir d’un <xref:System.Windows.Navigation.NavigationWindow> ou d’un <xref:System.Windows.Controls.Frame> dans une application autonome est implémentée en fonction de l’infrastructure d’hébergement du navigateur WPF, impliquant le processus PresentationHost, le niveau de sécurité est légèrement inférieur à celui que le contenu est chargé directement dans Internet Explorer sur Windows Vista et Windows 7 (ce qui serait toujours par le biais de PresentationHost). En effet, une application WPF autonome utilisant un navigateur web ne fournit pas la fonctionnalité de sécurité supplémentaire du mode protégé d’Internet Explorer.  
  
<a name="BestPractices"></a>   
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Ressources pour le développement d’applications WPF promouvant la sécurité  
 Voici quelques ressources supplémentaires qui vous aideront à développer des applications WPF qui favorisent la sécurité :  
  
|Zone|Ressource|  
|----------|--------------|  
|Code managé|[Index des directives, conseils et procédures de sécurité pour les applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Sécurité d’accès du code](../misc/code-access-security.md)|  
|ClickOnce|[Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[Sécurité de confiance partielle de WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de confiance partielle de WPF](wpf-partial-trust-security.md)
- [Stratégie de sécurité de WPF - sécurité de la plateforme](wpf-security-strategy-platform-security.md)
- [Stratégie de sécurité de WPF - ingénierie de sécurité](wpf-security-strategy-security-engineering.md)
- [Index des directives, conseils et procédures de sécurité pour les applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Sécurité d’accès du code](../misc/code-access-security.md)
- [Sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)
- [Vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
