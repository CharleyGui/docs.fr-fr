---
title: Sécurité de confiance partielle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 0d9bbcc32eea49afc6ecc713b0cf005b4434a67d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743331"
---
# <a name="wpf-partial-trust-security"></a>Sécurité de confiance partielle de WPF
<a name="introduction"></a> En général, les applications Internet doivent disposer d’un accès direct limité aux ressources système critiques, afin d’éviter des dommages dus à des actes de malveillance. Par défaut, les langages de script HTML et côté client ne sont pas en mesure d’accéder aux ressources système critiques. Étant donné que les applications hébergées par un navigateur Windows Presentation Foundation (WPF) peuvent être lancées à partir du navigateur, elles doivent être conformes à un ensemble similaire de restrictions. Pour appliquer ces restrictions, WPF s’appuie sur la sécurité d’accès du code (CAS) et ClickOnce (consultez [stratégie de sécurité de WPF-sécurité](wpf-security-strategy-platform-security.md)de la plateforme). Par défaut, les applications hébergées par un navigateur demandent le jeu d’autorisations de la zone Internet, qu’elles soient lancées à partir d’Internet, de l’intranet local ou de l’ordinateur local. Les applications qui sont exécutées sans jeu d’autorisations complet sont exécutées avec une confiance dite partielle.  
  
 WPF offre une grande variété de prise en charge pour garantir que le plus grand nombre possible de fonctionnalités pouvant être utilisées en toute sécurité avec une confiance partielle, et avec les autorités de certification, offre une prise en charge supplémentaire de la programmation de confiance partielle.  
  
 Cette rubrique contient les sections suivantes :  
  
- [Prise en charge de la confiance partielle avec des fonctionnalités WPF](#WPF_Feature_Partial_Trust_Support)  
  
- [Programmation de la confiance partielle](#Partial_Trust_Programming)  
  
- [Gestion des autorisations](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>Prise en charge de la confiance partielle avec des fonctionnalités WPF  
 Le tableau suivant répertorie les fonctionnalités de haut niveau de Windows Presentation Foundation (WPF) qui peuvent être utilisées en toute sécurité dans les limites du jeu d’autorisations de la zone Internet.  
  
 Tableau 1 : Fonctionnalités WPF pouvant être utilisées en toute sécurité avec une confiance partielle  
  
|Domaine de fonctionnalités|Composant|  
|------------------|-------------|  
|Général|Fenêtre du navigateur<br /><br /> Accès au site d’origine<br /><br /> IsolatedStorage (limité à 512 Ko)<br /><br /> Fournisseurs UIAutomation<br /><br /> Commandes<br /><br /> Éditeurs de méthode d’entrée (IME)<br /><br /> Stylet et entrée manuscrite<br /><br /> Glisser-déplacer simulé à l’aide d’événements de capture de la souris et de déplacement<br /><br /> OpenFileDialog<br /><br /> Désérialisation XAML (à l’aide de XamlReader.Load)|  
|Intégration web|Boîte de dialogue de téléchargement dans un navigateur<br /><br /> Navigation de premier niveau lancée par l’utilisateur<br /><br /> mailto:Links<br /><br /> Paramètres de l’URI (Uniform Resource Identifier)<br /><br /> HTTPWebRequest<br /><br /> Contenu WPF hébergé dans un IFRAME<br /><br /> Hébergement de pages HTML d’un même site à l’aide d’un Frame<br /><br /> Hébergement de pages HTML d’un même site à l’aide d’un WebBrowser<br /><br /> Services web (ASMX)<br /><br /> Services web (utilisant Windows Communication Foundation)<br /><br /> Scripts<br /><br /> Document Object Model|  
|Objets visuels|2D et 3D<br /><br /> Animation<br /><br /> Média (site d’origine et interdomaines)<br /><br /> Images/Audio/Vidéo|  
|Lecture|FlowDocuments<br /><br /> Documents XPS<br /><br /> Polices système et incorporées<br /><br /> Polices CFF et TrueType|  
|Modification|Vérification de l’orthographe<br /><br /> RichTextBox<br /><br /> Prise en charge du Presse-papiers pour les entrées manuscrites et le texte en clair<br /><br /> Coller à l’initiative de l’utilisateur<br /><br /> Copie du contenu sélectionné|  
|Contrôles|Contrôles généraux|  
  
 Ce tableau couvre les fonctionnalités WPF à un niveau élevé. Pour obtenir des informations plus détaillées, le SDK Windows documente les autorisations requises par chaque membre dans WPF. De plus, les fonctionnalités suivantes proposent des informations plus détaillées concernant l’exécution en mode confiance partielle, notamment des considérations spéciales.  
  
- [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (consultez [vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)).  
  
- Fenêtres contextuelles (voir <xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>).  
  
- Glisser-déplacer (consultez [vue d’ensemble du glisser-déplacer](./advanced/drag-and-drop-overview.md)).  
  
- Presse-papiers (voir <xref:System.Windows.Clipboard?displayProperty=nameWithType>).  
  
- Création d’images (voir <xref:System.Windows.Controls.Image?displayProperty=nameWithType>).  
  
- Sérialisation (voir <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>, <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>).  
  
- Ouvrir un fichier, boîte de dialogue (voir <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>).  
  
 Le tableau suivant présente les fonctionnalités WPF qui ne peuvent pas être exécutées en toute sécurité dans les limites du jeu d’autorisations de la zone Internet.  
  
 Tableau 2 : Fonctionnalités WPF ne pouvant pas être utilisées en toute sécurité avec une confiance partielle  
  
|Domaine de fonctionnalités|Composant|  
|------------------|-------------|  
|Général|Fenêtre (boîtes de dialogue et fenêtres définies par l’application)<br /><br /> SaveFileDialog<br /><br /> Système de fichiers<br /><br /> Accès au Registre<br /><br /> Glisser-déplacer<br /><br /> Sérialisation XAML (à l’aide de XamlWriter.Save)<br /><br /> Clients UIAutomation<br /><br /> Accès à la fenêtre source (HwndHost)<br /><br /> Prise en charge vocale intégrale<br /><br /> Interopérabilité Windows Forms|  
|Objets visuels|Effets bitmap<br /><br /> Encodage d’images|  
|Modification|Presse-papiers RTF (Rich Text Format)<br /><br /> Prise en charge XAML intégrale|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>Programmation de la confiance partielle  
 Pour les applications XBAP, le code qui dépasse le jeu d’autorisations par défaut aura un comportement différent en fonction de la zone de sécurité. Dans certains cas, l’utilisateur reçoit un avertissement quand il tente de l’installer. Il peut choisir de continuer ou d’annuler l’installation. Le tableau suivant décrit le comportement de l’application pour chaque zone de sécurité et ce que vous devez faire pour que l’application reçoive la confiance totale.  
  
|Zone de sécurité|Comportement|Obtention de la confiance totale|  
|-------------------|--------------|------------------------|  
|Ordinateur local|Confiance totale automatique|Aucune action n’est requise.|  
|Intranet et sites de confiance|Invite pour la confiance totale|Signez l’application XBAP avec un certificat afin que l’utilisateur consulte la source dans l’invite.|  
|Internet|Échec avec "Confiance non accordée"|Signez l’application XBAP avec un certificat.|  
  
> [!NOTE]
> Le comportement décrit dans le tableau précédent concerne les applications XBAP de confiance totale qui ne suivent pas le modèle de déploiement approuvé ClickOnce.  
  
 En général, le code qui outrepasse les permissions autorisées est susceptible d’être du code commun qui est partagé entre des applications hébergées par le navigateur et des applications autonomes. Les autorités de certification et WPF offrent plusieurs techniques pour gérer ce scénario.  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>Détermination des autorisations à l’aide de la sécurité d’accès du code  
 Dans certains cas, il est possible que le code partagé dans les assemblys de bibliothèque soit utilisé par les applications autonomes et les applications XBAP. Le code risque alors d’exécuter des fonctionnalités qui pourraient nécessiter plus d’autorisations que celles accordées par le jeu d’autorisations de l’application. Votre application peut déterminer si elle dispose d’une autorisation spécifique à l’aide de la sécurité de Microsoft .NET Framework. Plus précisément, il peut déterminer s’il dispose d’une autorisation spécifique en appelant la méthode <xref:System.Security.CodeAccessPermission.Demand%2A> sur l’instance de l’autorisation souhaitée. Ce test est illustré dans l’exemple suivant, dans lequel le code vérifie s’il peut enregistrer un fichier sur le disque local :  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 Si une application n’a pas l’autorisation souhaitée, l’appel à <xref:System.Security.CodeAccessPermission.Demand%2A> lèvera une exception de sécurité. Sinon, l’autorisation a été accordée. `IsPermissionGranted` encapsule ce comportement et retourne `true` ou `false` selon le cas.  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>Dégradation progressive des fonctionnalités  
 Pour du code qui peut être exécuté à partir de différentes zones, il est intéressant de pouvoir déterminer si une autorisation de faire ce qu’il a besoin de faire lui est accordée ou non. Même si la détermination de la zone est un élément, il est de loin préférable de proposer, si possible, une alternative à l’utilisateur. Par exemple, une application de confiance totale permet généralement aux utilisateurs de créer des fichiers où ils le souhaitent, alors qu’une application de confiance partielle peut créer des fichiers uniquement dans un stockage isolé. Si le code permettant de créer un fichier figure dans un assembly qui est partagé à la fois par des applications de confiance totale (autonomes) et des applications de confiance partielle (hébergées par le navigateur), et que les utilisateurs doivent pouvoir créer des fichiers dans ces deux types d’applications, le code partagé doit déterminer s’il est exécuté avec une confiance partielle ou totale avant de créer un fichier à l’emplacement approprié. Le code suivant illustre ces deux cas de figure.  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 Dans de nombreux cas, vous devez pouvoir trouver une alternative à la confiance partielle.  
  
 Dans un environnement contrôlé, tel qu’un intranet, les infrastructures managées personnalisées peuvent être installées sur la base du client dans le Global Assembly Cache (GAC). Ces bibliothèques peuvent exécuter du code qui requiert une confiance totale et être référencées à partir d’applications qui ne bénéficient que d’une confiance partielle à l’aide de <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (pour plus d’informations, consultez [sécurité](security-wpf.md) et [stratégie de sécurité de WPF-sécurité](wpf-security-strategy-platform-security.md)de la plateforme).  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>Détermination de l’hôte de navigateur  
 L’utilisation des autorités de certification pour vérifier les autorisations est une technique appropriée lorsque vous devez vérifier par autorisation. Cette technique dépend toutefois de l’interception des exceptions dans le cadre d’un traitement normal, ce qui n’est généralement pas recommandé et peut entraîner des problèmes de performances. Au lieu de cela, si votre application de navigateur XAML (XBAP) s’exécute uniquement dans le bac à sable (sandbox) de la zone Internet, vous pouvez utiliser la propriété <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>, qui retourne true pour les applications de navigateur XAML (XBAP).  
  
> [!NOTE]
> <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> distingue uniquement si une application s’exécute dans un navigateur, et non le jeu d’autorisations avec lequel une application s’exécute.  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>Gestion des autorisations  
 Par défaut, les XBAP s’exécutent avec une confiance partielle (jeu d’autorisations de la zone Internet par défaut). En fonction des spécifications de l’application, il est toutefois possible de changer le jeu d’autorisations par défaut. Par exemple, si une applications XBAP est lancée à partir d’un intranet local, elle peut tirer parti d’un jeu d’autorisations accru, qui est indiqué dans le tableau suivant.  
  
 Tableau 3 : Autorisations LocalIntranet et Internet  
  
|Autorisation|Attribut|LocalIntranet|Internet|  
|----------------|---------------|-------------------|--------------|  
|DNS|Serveurs d’accès DNS|Oui|Non|  
|Variables d’environnement|Lecture|Oui|Non|  
|Boîtes de dialogue de fichiers|Ouvrir|Oui|Oui|  
|Boîtes de dialogue de fichiers|Unrestricted|Oui|Non|  
|Stockage isolé|Isolement de l’assembly par utilisateur|Oui|Non|  
|Stockage isolé|Isolement inconnu|Oui|Oui|  
|Stockage isolé|Quota utilisateur illimité|Oui|Non|  
|Support|Images, vidéo et audio sécurisés|Oui|Oui|  
|Impression|Impression par défaut|Oui|Non|  
|Impression|Impression sécurisée|Oui|Oui|  
|Réflexion|Émission|Oui|Non|  
|Sécurité|Exécution du code managé|Oui|Oui|  
|Sécurité|Déclarer des autorisations accordées|Oui|Non|  
|Interface utilisateur|Unrestricted|Oui|Non|  
|Interface utilisateur|Fenêtres de niveau supérieur sécurisées|Oui|Oui|  
|Interface utilisateur|Presse-papiers personnel|Oui|Oui|  
|Navigateur web|Navigation de frame sécurisée vers HTML|Oui|Oui|  
  
> [!NOTE]
> Le couper-coller est autorisé uniquement en mode confiance partielle quand il est à l’initiative de l’utilisateur.  
  
 Si vous devez augmenter le niveau d’autorisation, vous devez changer les paramètres du projet et le manifeste de l’application ClickOnce. Pour plus d’informations, consultez [Vue d’ensemble des applications de navigateur XAML](./app-development/wpf-xaml-browser-applications-overview.md). Les documents suivants peuvent également être utiles.  
  
- [Mage.exe (outil Manifest Generation and Editing)](../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
- [MageUI.exe (outil Manifest Generation and Editing, client graphique)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
- [Sécurisation des applications ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
 Si votre application XBAP requiert une confiance totale, vous pouvez utiliser les mêmes outils pour augmenter les autorisations demandées. Bien qu’une application XBAP ne reçoive la confiance totale que si elle est installée et lancée à partir de l’ordinateur local, de l’intranet ou à partir d’une URL qui est indiquée dans les sites approuvés ou autorisés du navigateur. Si l’application est installée à partir de l’intranet ou d’un site de confiance, l’utilisateur reçoit l’invite ClickOnce standard lui signalant les autorisations élevées. Il peut choisir de continuer ou d’annuler l’installation.  
  
 Vous pouvez également utiliser le modèle de déploiement approuvé ClickOnce pour le déploiement en mode confiance totale à partir de toute zone de sécurité. Pour plus d’informations, consultez [vue d’ensemble du déploiement d’applications approuvées](/visualstudio/deployment/trusted-application-deployment-overview) et [sécurité](security-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité](security-wpf.md)
- [Stratégie de sécurité de WPF - sécurité de la plateforme](wpf-security-strategy-platform-security.md)
- [Stratégie de sécurité de WPF - ingénierie de sécurité](wpf-security-strategy-security-engineering.md)
