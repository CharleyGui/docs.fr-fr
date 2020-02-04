---
title: Stratégie de sécurité de la plateforme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: 4fa01922c5c3097adb124d67272b9f449b70ada3
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979870"
---
# <a name="wpf-security-strategy---platform-security"></a>Stratégie de sécurité de WPF - sécurité de la plateforme
Bien que Windows Presentation Foundation (WPF) fournisse divers services de sécurité, il tire également parti des fonctionnalités de sécurité de la plateforme sous-jacente, qui inclut le système d’exploitation, le CLR et Internet Explorer. Ces couches se combinent pour fournir à WPF un modèle de sécurité renforcé et de défense en profondeur qui tente d’éviter tout point de défaillance unique, comme illustré dans la figure suivante :  
  
 ![Diagramme qui montre le modèle de sécurité WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Le reste de cette rubrique décrit les fonctionnalités de chacune de ces couches qui concernent spécifiquement WPF.  

## <a name="operating-system-security"></a>Sécurité du système d'exploitation  
Le cœur de Windows fournit plusieurs fonctionnalités de sécurité qui constituent la base de sécurité pour toutes les applications Windows, y compris celles créées avec WPF. Cette rubrique traite de l’ampleur de ces fonctionnalités de sécurité qui sont importantes pour WPF, ainsi que de la façon dont WPF s’y intègre pour fournir une défense en profondeur supplémentaire.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Outre un examen général et un renforcement de Windows, il existe trois fonctionnalités clés de Windows XP SP2 que nous aborderons dans cette rubrique :  
  
- Compilation /GS  
  
- Windows Update Microsoft.  
  
#### <a name="gs-compilation"></a>Compilation /GS  
 Windows XP SP2 offre une protection en recompilant de nombreuses bibliothèques système principales, y compris toutes les dépendances WPF, telles que le CLR, pour aider à atténuer les dépassements de mémoire tampon. Cela est accompli en utilisant le paramètre /GS avec le compilateur de ligne de commande C/C++. Même s'il est clairement préférable d'éviter les dépassements de mémoire, la compilation /GS fournit un exemple de défense en profondeur contre les vulnérabilités potentielles qui sont créées par inadvertance ou par malveillance par ces derniers.  
  
 Historiquement, les dépassements de mémoire tampon ont été la cause de nombreuses attaques de sécurité à fort impact. Un dépassement de mémoire tampon se produit quand un intrus tire parti d'une vulnérabilité de code qui autorise l'injection de code malveillant qui écrit au-delà des limites d'une mémoire tampon. Cela permet ensuite à un intrus de détourner le processus dans lequel s'exécute le code en remplaçant l'adresse de retour d'une fonction pour provoquer l'exécution du code de l'intrus. Le résultat est un code malveillant qui exécute du code arbitraire avec les mêmes privilèges que le processus détourné.  
  
 À un niveau élevé, l’indicateur-GS du compilateur protège contre les dépassements de mémoire tampon potentiels en injectant un cookie de sécurité spécial pour protéger l’adresse de retour d’une fonction qui a des mémoires tampon de chaînes locales. Après le retour d'une fonction, le cookie de sécurité est comparé à sa valeur précédente. Si la valeur a changé, cela signifie qu'un dépassement de mémoire tampon a pu se produire et le processus est arrêté avec une condition d'erreur. L'arrêt du processus empêche l'exécution de code potentiellement malveillant. Pour plus d’informations, consultez [-GS (vérification de la sécurité de la mémoire tampon)](/cpp/build/reference/gs-buffer-security-check) .  
  
 WPF est compilé avec l’indicateur/GS pour ajouter encore une couche de défense aux applications WPF.  
  
### <a name="windows-vista"></a>Windows Vista  
Les utilisateurs de WPF sur Windows Vista bénéficieront des améliorations de sécurité supplémentaires du système d’exploitation, notamment l’accès utilisateur avec privilèges minimum, les contrôles d’intégrité du code et l’isolation des privilèges.  
  
#### <a name="user-account-control-uac"></a>Contrôle de compte d'utilisateur (UAC)  
 Aujourd’hui, les utilisateurs de Windows ont tendance à s’exécuter avec des privilèges d’administrateur, car de nombreuses applications en ont besoin pour l’installation ou l’exécution, ou les deux. Le fait de pouvoir écrire les paramètres d'application par défaut dans le Registre en est un exemple.  
  
 Une exécution avec des privilèges d'administrateur signifie en réalité que les applications s'exécutent à partir de processus auxquels sont accordés des privilèges d'administrateur. L'impact de cela sur la sécurité est que tout code malveillant qui détourne un processus s'exécutant avec des privilèges d'administrateur héritera automatiquement de ces privilèges, y compris l'accès aux ressources système critiques.  
  
 Une façon de se protéger contre cette menace de sécurité est d'exécuter les applications avec le moins de privilèges requis. C’est ce que l’on appelle le principe du moindre privilège et qui est une fonctionnalité de base du système d’exploitation Windows. Cette fonctionnalité est appelée contrôle de compte d’utilisateur (UAC, User Account Control) et est utilisée par le contrôle de compte d’utilisateur Windows de deux manières principales :  
  
- Pour exécuter la plupart des applications avec les privilèges de contrôle de compte d'utilisateur par défaut, même si l'utilisateur est administrateur ; seules les applications qui ont besoin de privilèges d'administrateur s'exécuteront avec les privilèges d'administrateur. Pour s'exécuter avec des privilèges d'administrateur, les applications doivent être marquées explicitement dans leur manifeste d'application ou comme entrée dans la stratégie de sécurité.  
  
- Pour fournir des solutions de compatibilité comme la virtualisation. Par exemple, de nombreuses applications tentent d'écrire dans des emplacements restreints comme C:\Program Files. Pour les applications s'exécutant sous contrôle de compte d'utilisateur, il existe un autre emplacement par utilisateur dans lequel les opérations d'écriture ne nécessitent pas de privilèges d'administrateur. Pour les applications s'exécutant sous contrôle de compte d'utilisateur, cette fonctionnalité virtualise C:\Program Files de sorte que les applications qui pensent écrire à cet emplacement écrivent en réalité à l'autre emplacement utilisateur. Ce type de travail de compatibilité permet au système d'exploitation d'exécuter de nombreuses applications qui ne pouvaient pas s'exécuter précédemment dans le contrôle de compte d'utilisateur.  
  
#### <a name="code-integrity-checks"></a>Contrôles d'intégrité du code  
 Windows Vista intègre des contrôles d’intégrité du code plus approfondis pour empêcher l’injection de code malveillant dans les fichiers système ou dans le noyau au moment du chargement/exécution. Cela va au-delà de la protection des fichiers système.  
   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Processus de droits limités pour les applications hébergées par un navigateur  
 Les applications WPF hébergées par un navigateur s’exécutent dans le bac à sable de la zone Internet. L’intégration de WPF avec Microsoft Internet Explorer étend cette protection avec une prise en charge supplémentaire.  
  
 Étant donné que les applications de navigateur XAML (XBAP) sont généralement bac à sable (sandbox) par le jeu d’autorisations de la zone Internet, la suppression de ces privilèges n’endommage pas les applications de navigateur XAML (XBAP) du point de vue de la compatibilité. En revanche, une couche de défense en profondeur supplémentaire est créée. Si une application sandbox peut exploiter d'autres couches et détourner le processus, celui-ci aura encore des privilèges limités.  
  
 Consultez [utilisation d’un compte d’utilisateur doté de privilèges minimum](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Sécurité du Common Language Runtime  
 Le common language runtime (CLR) offre un certain nombre d’avantages de sécurité clés qui incluent la validation et la vérification, la sécurité d’accès du code (CAS) et la méthodologie critique de sécurité.  
    
### <a name="validation-and-verification"></a>Validation et vérification  
 Pour assurer l’isolation et l’intégrité des assemblys, le CLR utilise un processus de validation. La validation CLR garantit que les assemblys sont isolés en validant leur format de fichier exécutable portable (PE) pour les adresses qui pointent à l’extérieur de l’assembly. La validation CLR valide également l’intégrité des métadonnées incorporées dans un assembly.  
  
 Pour garantir la cohérence des types, empêcher les problèmes de sécurité courants (par exemple, les dépassements de mémoire tampon) et activer le sandboxing via l’isolation de sous-processus, la sécurité du CLR utilise le concept de vérification.  
  
 Les applications managées sont compilées en langage MSIL (Microsoft Intermediate Language). Quand les méthodes d'une application managée sont exécutées, son code MSIL est compilé en code natif par le biais de la compilation juste-à-temps (JIT). La compilation JIT inclut un processus de vérification qui applique de nombreuses règles de sécurité et de robustesse qui garantissent que le code :  
  
- ne viole pas les contrats des types ;  
  
- n'introduit pas de dépassements de mémoire tampon ;  
  
- n'accède pas intensément à la mémoire.  
  
 Le code managé qui ne se conforme pas aux règles de vérification n'est pas autorisé à s'exécuter, à moins qu'il soit considéré comme un code approuvé.  
  
 L’avantage du code vérifiable est la raison principale pour laquelle WPF s’appuie sur le .NET Framework. Dans la mesure où du code vérifiable est utilisé, la possibilité d'exploiter des failles éventuelles est considérablement réduite.  
  
### <a name="code-access-security"></a>Sécurité d'accès du code  
 Un ordinateur client expose une grande variété de ressources auxquelles une application managée peut avoir accès, notamment le système de fichiers, le Registre, les services d'impression, l'interface utilisateur, la réflexion et les variables d'environnement. Pour qu’une application managée puisse accéder aux ressources d’un ordinateur client, elle doit disposer de l’autorisation .NET Framework. Une autorisation dans les autorités de certification est une sous-classe du <xref:System.Security.CodeAccessPermission>; Les autorités de certification implémentent une sous-classe pour chaque ressource à laquelle les applications managées peuvent accéder.  
  
 Le jeu d’autorisations qu’une application managée est accordée par les autorités de certification lorsqu’elle commence à s’exécuter est appelé jeu d’autorisations et est déterminé par une preuve fournie par l’application. Pour les applications WPF, la preuve fournie est l’emplacement, ou zone, à partir duquel les applications sont lancées. Les autorités de certification identifient les zones suivantes :  
  
- **Poste de travail** : applications lancées à partir de l'ordinateur client (entièrement fiable).  
  
- **Intranet local** : applications lancées à partir de l'intranet (niveau de confiance moyen).  
  
- **Internet** : applications lancées à partir d'Internet (niveau de confiance le plus faible).  
  
- **Sites de confiance** : applications identifiées par un utilisateur comme dignes de confiance (niveau de confiance le plus faible).  
  
- **Sites non fiables** : applications identifiées par un utilisateur comme étant non fiables (non approuvé).  
  
 Pour chacune de ces zones, les autorités de certification fournissent un jeu d’autorisations prédéfini qui inclut les autorisations correspondant au niveau de confiance associé à chacun. Elles incluent notamment :  
  
- **FullTrust** : Pour les applications lancées à partir de la zone de **poste de travail** . Toutes les autorisations possibles sont accordées.  
  
- **LocalIntranet** : Pour les applications lancées à partir de la zone **Intranet local** . Un sous-ensemble d'autorisations est accordé pour fournir un accès modéré aux ressources d'un ordinateur client : emplacement de stockage isolé, accès illimité à l'interface utilisateur, accès illimité aux boîtes de dialogue de fichier, réflexion limitée et accès limité aux variables d'environnement. Les autorisations permettant d'accéder aux ressources critiques comme le Registre ne sont pas fournies.  
  
- **Internet** : Pour les applications lancées à partir de la zone **Internet** ou **sites de confiance** . Un sous-ensemble d'autorisations est accordé pour octroyer un accès limité aux ressources d'un ordinateur client : emplacement de stockage isolé, ouverture des fichiers uniquement et interface utilisateur limitée. Fondamentalement, ce jeu d’autorisations isole les applications de l’ordinateur client.  
  
 Les applications identifiées comme étant issues de la zone de **sites non fiables** ne bénéficient d’aucune autorisation par les autorités de certification. Par conséquent, il n'existe pas de jeu d'autorisations prédéfini pour ces applications.  
  
 La figure suivante illustre la relation entre les zones, les jeux d’autorisations, les autorisations et les ressources :  
  
 ![Diagramme qui affiche les jeux d’autorisations CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Les restrictions du bac à sable (sandbox) de sécurité de la zone Internet s’appliquent de la même manière à tout code qu’un XBAP importe à partir d’une bibliothèque système, y compris WPF. Cela garantit que chaque partie du code est verrouillée, même WPF. Malheureusement, pour pouvoir s’exécuter, une application XBAP doit exécuter des fonctionnalités qui nécessitent davantage d’autorisations que celles activées par le bac à sable (sandbox) de sécurité de la zone Internet.  
  
 Prenons l’exemple d’une application XBAP qui comprend la page suivante :  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Pour exécuter ce XBAP, le code WPF sous-jacent doit exécuter plus de fonctionnalités que ce qui est disponible pour le XBAP appelant, y compris :  
  
- Création d’un handle de fenêtre (HWND) pour le rendu  
  
- distribution de messages ;  
  
- chargement de la police Tahoma.  
  
 Du point de vue de la sécurité, il serait catastrophique d'autoriser l'application sandbox à accéder directement à l'une de ces opérations.  
  
 Heureusement, WPF répond à cette situation en autorisant l’exécution de ces opérations avec des privilèges élevés pour le compte de l’application bac à sable (sandbox). Alors que toutes les opérations WPF sont vérifiées par rapport aux autorisations de sécurité limitées de la zone Internet du domaine d’application de l’application XBAP, WPF (comme avec d’autres bibliothèques système) se voit accorder un jeu d’autorisations qui comprend toutes les autorisations possibles.
  
 Cela nécessite que WPF reçoive des privilèges élevés tout en empêchant ces privilèges d’être régis par le jeu d’autorisations de la zone Internet du domaine d’application hôte.  
  
 Pour ce faire, WPF utilise la méthode **Assert** d’une autorisation. Le code suivant en donne l'illustration.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 L' **assertion** empêche essentiellement les autorisations illimitées requises par WPF d’être limitées par les autorisations de la zone Internet de l’application XBAP.  
  
 Du point de vue de la plateforme, WPF est responsable de l’utilisation correcte de la méthode **Assert** . une utilisation incorrecte de la méthode **Assert** pourrait permettre à du code malveillant d’élever les privilèges. Par conséquent, il est important d’appeler uniquement une **assertion** quand cela est nécessaire, et de garantir que les restrictions du bac à sable (sandbox) restent intactes. Par exemple, le code en mode sandbox n'est pas autorisé à ouvrir des fichiers aléatoires, mais il est autorisé à utiliser des polices. WPF permet aux applications sandbox d’utiliser la fonctionnalité de police en appelant **Assert**, et à WPF de lire les fichiers connus pour contenir ces polices pour le compte de l’application bac à sable (sandbox).  
  
### <a name="clickonce-deployment"></a>déploiement ClickOnce  
 ClickOnce est une technologie de déploiement complète qui est incluse dans .NET Framework et s’intègre à Visual Studio (pour plus d’informations, consultez [sécurité et déploiement ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ). Les applications WPF autonomes peuvent être déployées à l’aide de ClickOnce, tandis que les applications hébergées par un navigateur doivent être déployées avec ClickOnce.  
  
 Les applications déployées à l’aide de ClickOnce reçoivent une couche de sécurité supplémentaire par rapport à la sécurité d’accès du code (CAS). Fondamentalement, les applications déployées par ClickOnce demandent les autorisations dont elles ont besoin. Seules ces autorisations leur sont accordées si elles ne dépassent pas le jeu d'autorisations pour la zone à partir de laquelle l'application est déployée. En réduisant le jeu d’autorisations à celles qui sont nécessaires, même si elles sont inférieures à celles fournies par le jeu d’autorisations de la zone de lancement, le nombre de ressources auxquelles l’application a accès est réduit au minimum. Par conséquent, si l'application est détournée, les risques de dommages sur l'ordinateur client sont réduits.  
  
### <a name="security-critical-methodology"></a>Méthodologie critique de sécurité  
 Le code WPF qui utilise des autorisations pour activer le bac à sable (sandbox) de la zone Internet pour les applications XBAP doit être maintenu au niveau d’audit et de contrôle de sécurité le plus élevé possible. Pour faciliter cette exigence, .NET Framework fournit une nouvelle prise en charge de la gestion du code qui élève les privilèges. Plus précisément, le CLR vous permet d’identifier le code qui élève le privilège et de le marquer avec l' <xref:System.Security.SecurityCriticalAttribute>; tout code non marqué avec <xref:System.Security.SecurityCriticalAttribute> devient *transparent* à l’aide de cette méthodologie. Inversement, le code managé qui n'est pas marqué avec <xref:System.Security.SecurityCriticalAttribute> est empêché d'élever le privilège.  
  
 La méthodologie critique de sécurité permet à l’organisation de code WPF qui élève le privilège dans le *noyau critique de sécurité*, le reste étant transparent. L’isolation du code critique de sécurité permet à l’équipe d’ingénierie WPF de concentrer une analyse de sécurité et un contrôle du code source supplémentaires sur le noyau critique de sécurité au-dessus et au-delà des pratiques de sécurité standard (consultez [stratégie de sécurité de WPF-ingénierie de sécurité](wpf-security-strategy-security-engineering.md)).  
  
 Notez que .NET Framework autorise le code de confiance à étendre le bac à sable (sandbox) de la zone Internet XBAP en permettant aux développeurs d’écrire des assemblys managés marqués avec <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) et déployés dans le global assembly cache (GAC) de l’utilisateur. Marquer un assembly avec APTCA est une opération de sécurité très sensible, car n'importe quel code peut appeler cet assembly, y compris du code malveillant en provenance d'Internet. Cette opération exige la plus grande prudence et le respect des meilleures pratiques. De plus, les utilisateurs doivent décider d'approuver ce logiciel pour pouvoir l'installer.  
  
## <a name="microsoft-internet-explorer-security"></a>Sécurité de Microsoft Internet Explorer  
 En plus de réduire les problèmes de sécurité et de simplifier la configuration de la sécurité, Microsoft Internet Explorer 6 (SP2) contient plusieurs fonctionnalités qui améliorent la sécurité pour les utilisateurs des applications de navigateur XAML (XBAP). L'idée-force de ces fonctionnalités est d'offrir aux utilisateurs un contrôle accru sur leur navigation.  
  
 Avant IE6 SP2, les utilisateurs pouvaient être soumis à l’un des éléments suivants :  
  
- affichage de fenêtres intempestives aléatoires ;  
  
- redirection de script confuse ;  
  
- nombreuses boîtes de dialogue de sécurité sur certains sites web.  
  
 Dans certains cas, les sites Web non fiables essaient de tromper les utilisateurs en usurpant l’installation [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ou en présentant plusieurs fois une boîte de dialogue d’installation Microsoft ActiveX, même si l’utilisateur peut l’avoir annulée. Il possible que ces techniques aient amené un nombre significatif d'utilisateurs à prendre de mauvaises décisions aboutissant à l'installation de logiciels espions.  
  
 IE6 SP2 comprend plusieurs fonctionnalités permettant d’atténuer ces types de problèmes, qui tournent autour du concept d’initiation de l’utilisateur. IE6 SP2 détecte quand un utilisateur clique sur un lien ou un élément de page avant une action, appelée « initiation de l' *utilisateur*», et le traite différemment lorsqu’une action similaire est déclenchée par le script sur une page. Par exemple, IE6 SP2 incorpore un **bloqueur de fenêtres publicitaires** qui détecte quand un utilisateur clique sur un bouton avant que la page crée une fenêtre contextuelle. Cela permet à IE6 SP2 d’autoriser les fenêtres contextuelles les plus inoffensives tout en empêchant les fenêtres contextuelles que les utilisateurs ne demandent pas ou n’ont pas souhaité. Les fenêtres contextuelles bloquées sont interceptées sous la nouvelle **barre d’informations**, ce qui permet à l’utilisateur de remplacer manuellement le bloc et d’afficher la fenêtre contextuelle.  
  
 La même logique d’initiation d’utilisateur est également appliquée pour **ouvrir**/**Enregistrer** les invites de sécurité. Les boîtes de dialogue d’installation ActiveX sont toujours interceptées sous la barre d’informations, sauf si elles représentent une mise à niveau à partir d’un contrôle installé précédemment. Ces mesures se combinent pour donner à l'utilisateur une expérience plus sûre et mieux contrôlée, puisqu'ils sont protégés contre les sites qui les poussent à installer des logiciels indésirables ou malveillants.  
  
 Ces fonctionnalités protègent également les clients qui utilisent IE6 SP2 pour accéder aux sites Web qui leur permettent de télécharger et d’installer des applications WPF. En particulier, il s’agit du fait que IE6 SP2 offre une meilleure expérience utilisateur qui réduit le risque que les utilisateurs installent des applications malveillantes ou détentes, quelle que soit la technologie utilisée pour les créer, y compris WPF. WPF ajoute à ces protections à l’aide de ClickOnce pour faciliter le téléchargement de ses applications sur Internet. Étant donné que les applications de navigateur XAML (XBAP) s’exécutent dans un bac à sable (sandbox) de sécurité de zone Internet, elles peuvent être lancées en toute transparence. En revanche, les applications WPF autonomes requièrent une confiance totale pour s’exécuter. Pour ces applications, ClickOnce affiche une boîte de dialogue de sécurité pendant le processus de lancement pour notifier l’utilisation des exigences de sécurité supplémentaires de l’application. Cependant, cette opération nécessite également l'intervention de l'utilisateur et peut être annulée.  
  
 Internet Explorer 7 intègre et étend les fonctionnalités de sécurité d’IE6 SP2 dans le cadre d’un engagement continu pour la sécurité.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès du code](../misc/code-access-security.md)
- [Security](security-wpf.md)
- [Sécurité de confiance partielle de WPF](wpf-partial-trust-security.md)
- [Stratégie de sécurité de WPF - ingénierie de sécurité](wpf-security-strategy-security-engineering.md)
