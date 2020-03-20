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
ms.openlocfilehash: e0a56dcbf8d151fcb0d4f6271ecba15c0ff955a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174613"
---
# <a name="security-wpf"></a>Sécurité (WPF)
<a name="introduction"></a>Lorsque vous développez des applications autonomes et hébergées par le navigateur de la Windows Presentation Foundation (WPF), vous devez tenir compte du modèle de sécurité. Les applications autonomes WPF s’exécutent avec des autorisations sans restriction (ensemble d’autorisations**CAS FullTrust),** qu’elles soient déployées à l’aide de Windows Installer (.msi), XCopy ou ClickOnce. Le déploiement d’applications WPF autonomes de confiance partielle avec ClickOnce n’est pas pris en charge. Cependant, une application d’hôte pleine confiance <xref:System.AppDomain> peut créer une fiducie partielle à l’aide du modèle .NET Framework Add-in. Pour plus d’informations, voir [WPF Add-Ins Overview](./app-development/wpf-add-ins-overview.md).  
  
 Les applications hébergées par navigateur WPF sont hébergées par Windows Internet Explorer ou Firefox, et [!INCLUDE[TLA#tla_xaml](../../../includes/tlasharptla-xaml-md.md)] peuvent être soit des applications de navigateur XAML (XBAPs) ou des documents en vrac Pour plus d’informations, voir [WPF XAML Browser Applications Overview](./app-development/wpf-xaml-browser-applications-overview.md).  
  
 Les applications hébergées par navigateur WPF s’exécutent dans un bac à sable partiel de sécurité de confiance, par défaut, qui est limitée à l’ensemble d’autorisations**Internet** par défaut du CAS. Cela isole efficacement les applications hébergées par le navigateur WPF de l’ordinateur client de la même manière que vous vous attendez à ce que les applications Web typiques soient isolées. Une application XBAP peut élever des privilèges jusqu’à la confiance totale, selon la zone de sécurité de l’URL de déploiement et la configuration de sécurité du client. Pour plus d’informations, consultez [Sécurité de confiance partielle de WPF](wpf-partial-trust-security.md).  
  
 Ce sujet traite du modèle de sécurité des applications autonomes et hébergées par le navigateur de la Windows Presentation Foundation (WPF).  
  
 Cette rubrique contient les sections suivantes :  
  
- [Sécurité de la navigation](#SafeTopLevelNavigation)  
  
- [Paramètres de sécurité des logiciels de navigation web](#InternetExplorerSecuritySettings)  
  
- [Contrôle WebBrowser et contrôles de fonctionnalités](#webbrowser_control_and_feature_controls)  
  
- [Désactivation des assemblys APTCA pour les applications clientes partiellement fiables](#APTCA)  
  
- [Comportement de bac à sable pour les fichiers en XAML libre](#LooseContentSandboxing)  
  
- [Ressources pour le développement d’applications WPF promouvant la sécurité](#BestPractices)  
  
<a name="SafeTopLevelNavigation"></a>
## <a name="safe-navigation"></a>Sécurité de la navigation  
 Pour les XAP, WPF distingue deux types de navigation : l’application et le navigateur.  
  
 La *navigation dans une application* est la navigation entre les éléments de contenu dans une application hébergée par un navigateur. La *navigation dans un navigateur* est la navigation qui modifie l’URL de contenu et d’emplacement d’un navigateur lui-même. La relation entre la navigation d’application (généralement XAML) et la navigation du navigateur (généralement HTML) est affichée dans l’illustration suivante :
  
 ![Relation entre la navigation d’application et la navigation par navigateur.](./media/security-wpf/application-browser-navigation-relationship.png)  
  
 Le type de contenu considéré comme sûr pour un XBAP à naviguer à est principalement déterminé par si la navigation d’application ou la navigation par navigateur est utilisé.  
  
<a name="Application_Navigation_Security"></a>
### <a name="application-navigation-security"></a>Sécurité de la navigation dans une application  
 La navigation d’application est considérée comme sûre si elle peut être identifiée avec un pack URI, qui prend en charge quatre types de contenu :  
  
|Type de contenu|Description|Exemple d’URI|  
|------------------|-----------------|-----------------|  
|Ressource|Fichiers qui sont ajoutés à un projet avec un type de construction de **ressource**.|`pack://application:,,,/MyResourceFile.xaml`|  
|Contenu|Fichiers qui sont ajoutés à un projet avec un type de **contenu**de construction .|`pack://application:,,,/MyContentFile.xaml`|  
|Site d’origine|Fichiers qui sont ajoutés à un projet avec un type de construction de **None**.|`pack://siteoforigin:,,,/MySiteOfOriginFile.xaml`|  
|Code de l’application|Ressources XAML avec un code-behind compilé.<br /><br /> -ou-<br /><br /> Fichiers XAML qui sont ajoutés à un projet avec un type de build de **Page**.|`pack://application:,,,/MyResourceFile` `.xaml`|  
  
> [!NOTE]
> Pour plus d’informations sur les fichiers de données d’application et les URL de l’emballage, consultez [WPF Application Resource, Content, and Data Files](./app-development/wpf-application-resource-content-and-data-files.md).  
  
 Les fichiers ayant ces types de contenu sont accessibles par l’utilisateur et par programme :  
  
- **Navigation utilisateur**. L’utilisateur navigue en <xref:System.Windows.Documents.Hyperlink> cliquant sur un élément.  
  
- **Navigation par programme**. L’application navigue sans impliquer l’utilisateur, <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType> par exemple, en définissant la propriété.  
  
<a name="Browser_Navigation_Security"></a>
### <a name="browser-navigation-security"></a>Sécurité de la navigation dans un navigateur  
 La navigation dans un navigateur est considérée comme sûre uniquement si les conditions suivantes sont respectées :  
  
- **Navigation utilisateur**. L’utilisateur navigue en <xref:System.Windows.Documents.Hyperlink> cliquant sur <xref:System.Windows.Navigation.NavigationWindow>un élément qui <xref:System.Windows.Controls.Frame>se trouve dans le principal, pas dans un nid .  
  
- **Zone**. Le contenu cible de la navigation se trouve sur Internet ou sur l’intranet local.  
  
- **Protocole**. Le protocole utilisé est soit **http**, **https**, **fichier**, ou **mailto**.  
  
 Si un XBAP tente de naviguer vers le contenu d’une manière qui ne se conforme pas à ces conditions, a <xref:System.Security.SecurityException> est jeté.  
  
<a name="InternetExplorerSecuritySettings"></a>
## <a name="web-browsing-software-security-settings"></a>Paramètres de sécurité des logiciels de navigation web  
 Les paramètres de sécurité de votre ordinateur déterminent l’accès accordé à n’importe quel logiciel de navigation web. Le logiciel de navigation Web comprend toute application ou composant qui utilise les API [WinINet](/windows/win32/wininet/portal) ou [UrlMon,](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa767916(v=vs.85)) y compris Internet Explorer et PresentationHost.exe.  
  
 Internet Explorer fournit un mécanisme par lequel vous pouvez configurer la fonctionnalité qui est autorisée à être exécutée par ou à partir d’Internet Explorer, y compris ce qui suit:  
  
- .NET Composants dépendants du cadre  
  
- Plug-ins et contrôles ActiveX  
  
- Téléchargements  
  
- Création de scripts  
  
- Authentification utilisateur  
  
 La collecte de fonctionnalités qui peuvent être sécurisées de cette manière est configurée sur une base par zone pour **l’Internet,** **Intranet**, **Sites de confiance,** et les zones **de sites restreints.** Les étapes suivantes décrivent comment configurer vos paramètres de sécurité :  
  
1. Ouvrez le **Panneau de configuration**.  
  
2. Cliquez sur **Réseau et Internet,** puis cliquez sur **Les options Internet**.  
  
     La boîte de dialogue Options Internet apparaît.  
  
3. Sur l’onglet **Sécurité,** sélectionnez la zone pour configurer les paramètres de sécurité.  
  
4. Cliquez sur le bouton **Niveau personnalisé.**  
  
     La boîte de dialogue **Paramètres de sécurité** apparaît et vous pouvez configurer les paramètres de sécurité de la zone sélectionnée.  
  
     ![Capture d’écran qui montre la boîte de dialogue Paramètres de sécurité.](./media/security-wpf/windows-presentation-foundation-security-settings.png)  
  
> [!NOTE]
> Vous pouvez également accéder à la boîte de dialogue Options Internet à partir d’Internet Explorer. Cliquez sur **Outils,** puis cliquez sur **Options Internet**.  
  
 En commençant par Windows Internet Explorer 7, les paramètres de sécurité suivants spécifiquement pour .NET Framework sont inclus:  
  
- **XAML libre**. Contrôle si Internet Explorer peut [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] naviguer vers et en vrac fichiers. (Options Activer, Désactiver et Demander).  
  
- **Applications du navigateur XAML**. Contrôle si Internet Explorer peut naviguer vers et exécuter des XBAP. (Options Activer, Désactiver et Demander).  
  
 Par défaut, ces paramètres sont tous activés pour **l’Internet,** **l’intranet local**et les zones **de sites de confiance,** et désactivés pour la zone **des sites restreints.**  
  
<a name="Security_Settings_for_IE6_and_Below"></a>
### <a name="security-related-wpf-registry-settings"></a>Paramètres du Registre WPF relatifs à la sécurité  
 Outre les paramètres de sécurité disponibles avec les options Internet, les valeurs de Registre suivantes sont disponibles pour le blocage sélectif de certaines fonctionnalités WPF liées à la sécurité. Les valeurs sont définies sous la clé suivante :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\Windows Presentation Foundation\Features`  
  
 Le tableau ci-dessous répertorie les valeurs qui peuvent être définies.  
  
|Nom de la valeur|Type de valeur|Données de la valeur|  
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
 Le contrôle <xref:System.Windows.Controls.WebBrowser> WPF peut être utilisé pour héberger du contenu Web. Le contrôle <xref:System.Windows.Controls.WebBrowser> WPF enveloppe le contrôle sous-jacent WebBrowser ActiveX. WPF fournit un certain soutien pour sécuriser <xref:System.Windows.Controls.WebBrowser> votre application lorsque vous utilisez le contrôle WPF pour héberger du contenu Web non fiable. Toutefois, certaines fonctionnalités de sécurité doivent <xref:System.Windows.Controls.WebBrowser> être appliquées directement par les applications utilisant le contrôle. Pour plus d’informations sur le contrôle WebBrowser ActiveX, voir [Aperçus et tutoriels de contrôle WebBrowser](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752041(v=vs.85)).  
  
> [!NOTE]
> Cette section s’applique également <xref:System.Windows.Controls.Frame> au <xref:System.Windows.Controls.WebBrowser> contrôle puisqu’elle utilise le pour naviguer vers le contenu HTML.  
  
 Si le <xref:System.Windows.Controls.WebBrowser> contrôle WPF est utilisé pour héberger du contenu Web <xref:System.AppDomain> non fiable, votre application doit utiliser une fiducie partielle pour aider à isoler votre code d’application du code de script HTML potentiellement malveillant. Cela est particulièrement vrai si votre application est en <xref:System.Windows.Controls.WebBrowser.InvokeScript%2A> interaction <xref:System.Windows.Controls.WebBrowser.ObjectForScripting%2A> avec le script hébergé en utilisant la méthode et la propriété. Pour plus d’informations, voir [WPF Add-Ins Overview](./app-development/wpf-add-ins-overview.md).  
  
 Si votre application utilise <xref:System.Windows.Controls.WebBrowser> le contrôle WPF, une autre façon d’accroître la sécurité et d’atténuer les attaques est d’activer les contrôles de fonctionnalités Internet Explorer. Les contrôles de fonctionnalités sont des ajouts à Internet Explorer qui permettent aux administrateurs et aux développeurs de <xref:System.Windows.Controls.WebBrowser> configurer les fonctionnalités d’Internet Explorer et les applications qui hébergent le contrôle WebBrowser ActiveX, que le contrôle WPF enveloppe. Les contrôles de fonctionnalité peuvent être configurés en utilisant la fonction [CoInternetSetFeatureEnabled](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537168(v=vs.85)) ou en changeant les valeurs du registre. Pour plus d’informations sur les contrôles de fonctionnalités, voir [Introduction to Feature Controls](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms537184(v=vs.85)) et Internet Feature [Controls](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/general-info/ee330720(v=vs.85)).  
  
 Si vous développez une application WPF autonome <xref:System.Windows.Controls.WebBrowser> qui utilise le contrôle WPF, WPF permet automatiquement les contrôles de fonctionnalités suivants pour votre application.  
  
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
  
 Les contrôles de fonctionnalités sont appliqués par le processus d’instantané de l’objet WebBrowser ActiveX. Par conséquent, si vous créez une application autonome qui peut accéder à un contenu non approuvé, vous devez sérieusement envisager d’activer des contrôles de fonctionnalités supplémentaires.  
  
> [!NOTE]
> Cette recommandation est basée sur les recommandations générales sur la sécurité des hôtes MSHTML et SHDOCVW. Pour plus d’informations, voir [The MSHTML Host Security FAQ: Part I of II](https://msrc-blog.microsoft.com/2009/04/02/the-mshtml-host-security-faq-part-i-of-ii/) et The [MSHTML Host Security FAQ: Part II of II](https://msrc-blog.microsoft.com/2009/04/03/the-mshtml-host-security-faq-part-ii-of-ii/).  
  
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
  
 Si vous exécutez une application de navigateur XAML de confiance <xref:System.Windows.Controls.WebBrowser> partielle (XBAP) qui inclut un contrôle WPF dans Windows Internet Explorer, WPF héberge le contrôle WebBrowser ActiveX dans l’espace d’adresse du processus Internet Explorer. Étant donné que le contrôle WebBrowser ActiveX est hébergé dans le processus Internet Explorer, tous les contrôles de fonctionnalités pour Internet Explorer sont également activés pour le contrôle WebBrowser ActiveX.  
  
 Les applications XBAP exécutées dans Internet Explorer bénéficient également d’un niveau de sécurité supplémentaire par rapport aux applications autonomes normales. Cette sécurité supplémentaire est parce que Internet Explorer, et donc le contrôle WebBrowser ActiveX, fonctionne en mode protégé par défaut sur Windows Vista et Windows 7. Pour plus d’informations sur le mode protégé, voir [Comprendre et travailler en mode protégé Internet Explorer](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/).  
  
> [!NOTE]
> Si vous essayez d’exécuter un XBAP qui comprend un contrôle WPF <xref:System.Windows.Controls.WebBrowser> dans Firefox, tandis que dans la zone Internet, un <xref:System.Security.SecurityException> sera jeté. conformément à la stratégie de sécurité de WPF.  
  
<a name="APTCA"></a>
## <a name="disabling-aptca-assemblies-for-partially-trusted-client-applications"></a>Désactivation des assemblys APTCA pour les applications clientes partiellement fiables  
 Lorsque des assemblages gérés sont installés dans le cache d’assemblage global (GAC), ils deviennent pleinement dignes de confiance parce que l’utilisateur doit fournir une autorisation explicite pour les installer. Dans la mesure où ils sont entièrement fiables, seules les applications clientes managées entièrement fiables peuvent les utiliser. Pour permettre aux applications partiellement fiables de <xref:System.Security.AllowPartiallyTrustedCallersAttribute> les utiliser, elles doivent être marquées par l’APTCA. Seuls les assemblys dont la sécurité d’exécution a été testée pour une confiance partielle doivent être marqués avec cet attribut.  
  
 Cependant, il est possible pour un assemblage APTCA de présenter une faille de sécurité après avoir été installé dans le GAC . Lorsqu’une faille de sécurité est découverte, les éditeurs d’assembly peuvent produire une mise à jour de sécurité pour résoudre le problème sur les installations existantes et pour assurer une protection vis-à-vis des installations effectuées après la détection du problème. Pour la mise à jour, une option consiste à désinstaller l’assembly, bien que cela risque de bloquer d’autres applications clientes entièrement fiables qui utilisent l’assembly.  
  
 WPF fournit un mécanisme par lequel un assemblage APTCA peut être désactivé pour les XBAP partiellement fiables sans désinstaller l’assemblage APTCA.  
  
 Pour désactiver un assembly APTCA, vous devez créer une clé de Registre spéciale :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\<AssemblyFullName>, FileVersion=<AssemblyFileVersion>`  
  
 Un exemple est fourni ci-après :  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\policy\APTCA\aptcagac, Version=1.0.0.0, Culture=neutral, PublicKeyToken=215e3ac809a0fea7, FileVersion=1.0.0.0`  
  
 Cette clé établit une entrée pour l’assembly APTCA. Vous devez également créer une valeur dans cette clé, qui active ou désactive l’assembly. Voici les détails de la valeur :  
  
- Nom de la valeur: **APTCA_FLAG**.  
  
- Type de valeur: **REG_DWORD**.  
  
- Données sur la valeur : **1** à désactiver; **0** pour permettre.  
  
 Si un assembly doit être désactivé pour des applications clientes partiellement fiables, vous pouvez écrire une mise à jour qui crée la clé de Registre et la valeur.  
  
> [!NOTE]
> Les assemblages cadres de base .NET ne sont pas affectés par leur désactivation de cette façon parce qu’ils sont nécessaires pour que les applications gérées s’exécutent. La prise en charge de la désactivation des assemblys APTCA est principalement destinée aux applications tierces.  
  
<a name="LooseContentSandboxing"></a>
## <a name="sandbox-behavior-for-loose-xaml-files"></a>Comportement de bac à sable pour les fichiers en XAML libre  
 Les [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] fichiers en vrac sont des fichiers XAML de balisage seulement qui ne dépendent pas d’un code-derrière, gestionnaire d’événements, ou l’assemblage spécifique à l’application. Lorsque [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] les fichiers en vrac sont navigués directement à partir du navigateur, ils sont chargés dans un bac à sable de sécurité basé sur l’ensemble d’autorisation de zone Internet par défaut.  
  
 Cependant, le comportement de [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] sécurité est différent lorsque <xref:System.Windows.Navigation.NavigationWindow> les <xref:System.Windows.Controls.Frame> fichiers en vrac sont navigués à partir d’un ou dans une application autonome.  
  
 Dans les deux [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] cas, le fichier en vrac qui est navigué pour hérite des autorisations de sa demande d’hôte. Cependant, ce comportement peut être indésirable du point de [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] vue de la sécurité, en particulier si un fichier lâche a été produit par une entité qui n’est pas digne de confiance ou inconnue. Ce type de contenu est connu <xref:System.Windows.Controls.Frame> sous <xref:System.Windows.Navigation.NavigationWindow> le nom de *contenu externe,* et à la fois et peut être configuré pour l’isoler lorsqu’il est navigué vers. L’isolement est atteint en définissant la propriété **SandboxExternalContent** à vrai, comme le montrent les exemples suivants pour <xref:System.Windows.Controls.Frame> et <xref:System.Windows.Navigation.NavigationWindow>:  
  
 [!code-xaml[SecurityOverviewSnippets#FrameMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window2.xaml#framemarkup)]  
  
 [!code-xaml[SecurityOverviewSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/SecurityOverviewSnippets/CS/Window1.xaml#navigationwindowmarkup)]  
  
 Avec ce paramétrage, le contenu externe sera chargé dans un processus distinct du processus qui héberge l’application. Ce processus, limité au jeu d’autorisations de la zone Internet par défaut, l’isole efficacement de l’application d’hébergement et de l’ordinateur client.  
  
> [!NOTE]
> Même si la [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] navigation vers <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Frame> des fichiers en vrac à partir d’une application autonome ou dans une application autonome est implémentée en fonction de l’infrastructure d’hébergement du navigateur WPF, impliquant le processus PresentationHost, le niveau de sécurité est légèrement inférieur au moment où le contenu est chargé directement dans Internet Explorer sur Windows Vista et Windows 7 (qui serait toujours par PresentationHost). En effet, une application WPF autonome utilisant un navigateur web ne fournit pas la fonctionnalité de sécurité supplémentaire du mode protégé d’Internet Explorer.  
  
<a name="BestPractices"></a>
## <a name="resources-for-developing-wpf-applications-that-promote-security"></a>Ressources pour le développement d’applications WPF promouvant la sécurité  
 Voici quelques ressources supplémentaires pour aider à développer des applications WPF qui favorisent la sécurité :  
  
|Domaine|Ressource|  
|----------|--------------|  
|Code managé|[Index des directives, conseils et procédures de sécurité pour les applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))|  
|CAS|[Sécurité d’accès au code](../misc/code-access-security.md)|  
|ClickOnce|[ClickOnce Sécurité et déploiement](/visualstudio/deployment/clickonce-security-and-deployment)|  
|WPF|[Sécurité de confiance partielle WPF](wpf-partial-trust-security.md)|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de confiance partielle WPF](wpf-partial-trust-security.md)
- [Stratégie de sécurité de WPF - sécurité de la plateforme](wpf-security-strategy-platform-security.md)
- [Stratégie de sécurité de WPF - ingénierie de sécurité](wpf-security-strategy-security-engineering.md)
- [Index des directives, conseils et procédures de sécurité pour les applications](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))
- [Sécurité d’accès au code](../misc/code-access-security.md)
- [ClickOnce Sécurité et déploiement](/visualstudio/deployment/clickonce-security-and-deployment)
- [Vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
