---
title: Stratégie de sécurité de la plate-forme
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
ms.openlocfilehash: 258fcd7c51ea59de03fe60a4eeb9a82dd1c7efca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174600"
---
# <a name="wpf-security-strategy---platform-security"></a>Stratégie de sécurité de WPF - sécurité de la plateforme
Bien que Windows Presentation Foundation (WPF) fournisse une variété de services de sécurité, il tire également parti des caractéristiques de sécurité de la plate-forme sous-jacente, qui comprend le système d’exploitation, le CLR et Internet Explorer. Ces couches se combinent pour fournir à WPF un modèle de sécurité solide et en profondeur qui tente d’éviter tout point de défaillance unique, comme le montre le chiffre suivant :  
  
 ![Diagramme qui montre le modèle de sécurité WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Le reste de ce sujet traite des caractéristiques de chacune de ces couches qui se rapportent spécifiquement à WPF.  

## <a name="operating-system-security"></a>Sécurité du système d'exploitation  
Le cœur de Windows fournit plusieurs fonctionnalités de sécurité qui forment la base de sécurité pour toutes les applications Windows, y compris celles construites avec WPF. Ce sujet traite de l’étendue de ces caractéristiques de sécurité qui sont importantes pour WPF, ainsi que la façon dont WPF s’intègre avec eux pour fournir une défense plus approfondie.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 En plus d’un examen général et le renforcement de Windows, il ya trois fonctionnalités clés de Windows XP SP2 que nous allons discuter dans ce sujet:  
  
- Compilation /GS  
  
- Microsoft Windows Mise à jour.  
  
#### <a name="gs-compilation"></a>Compilation /GS  
 Windows XP SP2 offre une protection en reconstruisant de nombreuses bibliothèques de systèmes de base, y compris toutes les dépendances WPF telles que le CLR, pour aider à atténuer les dépassements de tampon. Cela est accompli en utilisant le paramètre /GS avec le compilateur de ligne de commande C/C++. Même s'il est clairement préférable d'éviter les dépassements de mémoire, la compilation /GS fournit un exemple de défense en profondeur contre les vulnérabilités potentielles qui sont créées par inadvertance ou par malveillance par ces derniers.  
  
 Historiquement, les dépassements de mémoire tampon ont été la cause de nombreuses attaques de sécurité à fort impact. Un dépassement de mémoire tampon se produit quand un intrus tire parti d'une vulnérabilité de code qui autorise l'injection de code malveillant qui écrit au-delà des limites d'une mémoire tampon. Cela permet ensuite à un intrus de détourner le processus dans lequel s'exécute le code en remplaçant l'adresse de retour d'une fonction pour provoquer l'exécution du code de l'intrus. Le résultat est un code malveillant qui exécute du code arbitraire avec les mêmes privilèges que le processus détourné.  
  
 À un niveau élevé, le drapeau compilateur -GS protège contre certains dépassements de tampon potentiels en injectant un cookie de sécurité spécial pour protéger l’adresse de retour d’une fonction qui a des tampons de chaîne locale. Après le retour d'une fonction, le cookie de sécurité est comparé à sa valeur précédente. Si la valeur a changé, cela signifie qu'un dépassement de mémoire tampon a pu se produire et le processus est arrêté avec une condition d'erreur. L'arrêt du processus empêche l'exécution de code potentiellement malveillant. Voir [-GS (Buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) pour plus de détails.  
  
 WPF est compilé avec le drapeau /GS pour ajouter encore une autre couche de défense aux applications WPF.  
  
### <a name="windows-vista"></a>Windows Vista  
Les utilisateurs de WPF sur Windows Vista bénéficieront des améliorations de sécurité supplémentaires du système d’exploitation, y compris « Access utilisateur le moins privilégié », des vérifications de l’intégrité du code et de l’isolement des privilèges.  
  
#### <a name="user-account-control-uac"></a>Contrôle de compte d'utilisateur (UAC)  
 Aujourd’hui, les utilisateurs de Windows ont tendance à s’exécuter avec des privilèges d’administrateur parce que de nombreuses applications les exigent pour l’installation ou l’exécution, ou les deux. Le fait de pouvoir écrire les paramètres d'application par défaut dans le Registre en est un exemple.  
  
 Une exécution avec des privilèges d'administrateur signifie en réalité que les applications s'exécutent à partir de processus auxquels sont accordés des privilèges d'administrateur. L'impact de cela sur la sécurité est que tout code malveillant qui détourne un processus s'exécutant avec des privilèges d'administrateur héritera automatiquement de ces privilèges, y compris l'accès aux ressources système critiques.  
  
 Une façon de se protéger contre cette menace de sécurité est d'exécuter les applications avec le moins de privilèges requis. C’est ce qu’on appelle le principe du moindre privilège, et est une caractéristique essentielle du système d’exploitation Windows. Cette fonctionnalité est appelée Contrôle des comptes utilisateur (UAC), et est utilisée par Windows UAC de deux façons principales:  
  
- Pour exécuter la plupart des applications avec les privilèges de contrôle de compte d'utilisateur par défaut, même si l'utilisateur est administrateur ; seules les applications qui ont besoin de privilèges d'administrateur s'exécuteront avec les privilèges d'administrateur. Pour s'exécuter avec des privilèges d'administrateur, les applications doivent être marquées explicitement dans leur manifeste d'application ou comme entrée dans la stratégie de sécurité.  
  
- Pour fournir des solutions de compatibilité comme la virtualisation. Par exemple, de nombreuses applications tentent d'écrire dans des emplacements restreints comme C:\Program Files. Pour les applications s'exécutant sous contrôle de compte d'utilisateur, il existe un autre emplacement par utilisateur dans lequel les opérations d'écriture ne nécessitent pas de privilèges d'administrateur. Pour les applications s'exécutant sous contrôle de compte d'utilisateur, cette fonctionnalité virtualise C:\Program Files de sorte que les applications qui pensent écrire à cet emplacement écrivent en réalité à l'autre emplacement utilisateur. Ce type de travail de compatibilité permet au système d'exploitation d'exécuter de nombreuses applications qui ne pouvaient pas s'exécuter précédemment dans le contrôle de compte d'utilisateur.  
  
#### <a name="code-integrity-checks"></a>Contrôles d'intégrité du code  
 Windows Vista intègre des contrôles d’intégrité de code plus profonds pour aider à empêcher le code malveillant d’être injecté dans les fichiers du système ou dans le noyau au moment de la charge / exécution. Cela va au-delà de la protection des fichiers système.  

### <a name="limited-rights-process-for-browser-hosted-applications"></a>Processus de droits limités pour les applications hébergées par un navigateur  
 Les applications WPF hébergées par navigateur s’exécutent dans le bac à sable de la zone Internet. L’intégration de WPF avec Microsoft Internet Explorer étend cette protection avec un support supplémentaire.  
  
 Étant donné que les applications de navigateur XAML (XBAP) sont généralement sandboxées par l’ensemble d’autorisation de zone Internet, la suppression de ces privilèges ne nuit pas aux applications de navigateur XAML (XBAP) du point de vue de la compatibilité. En revanche, une couche de défense en profondeur supplémentaire est créée. Si une application sandbox peut exploiter d'autres couches et détourner le processus, celui-ci aura encore des privilèges limités.  
  
 Voir [à l’aide d’un compte utilisateur le moins privilégié](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Sécurité du Common Language Runtime  
 L’heure courante de l’exécution de langue (CLR) offre un certain nombre d’avantages clés de sécurité qui incluent la validation et la vérification, la sécurité d’accès au code (CAS), et la méthodologie critique de sécurité.  

### <a name="validation-and-verification"></a>Validation et vérification  
 Pour assurer l’isolement et l’intégrité de l’assemblage, le CLR utilise un processus de validation. La validation CLR garantit que les assemblages sont isolés en validant leur format de fichier portable exécutable (PE) pour les adresses qui pointent en dehors de l’assemblage. La validation CLR valide également l’intégrité des métadonnées intégrées dans un assemblage.  
  
 Pour assurer la sécurité de type, aider à prévenir les problèmes de sécurité courants (p. ex. dépassements de tampons) et permettre le bac à sable par l’isolement des sous-traitants, la sécurité CLR utilise le concept de vérification.  
  
 Les applications managées sont compilées en langage MSIL (Microsoft Intermediate Language). Quand les méthodes d'une application managée sont exécutées, son code MSIL est compilé en code natif par le biais de la compilation juste-à-temps (JIT). La compilation JIT inclut un processus de vérification qui applique de nombreuses règles de sécurité et de robustesse qui garantissent que le code :  
  
- ne viole pas les contrats des types ;  
  
- n'introduit pas de dépassements de mémoire tampon ;  
  
- n'accède pas intensément à la mémoire.  
  
 Le code managé qui ne se conforme pas aux règles de vérification n'est pas autorisé à s'exécuter, à moins qu'il soit considéré comme un code approuvé.  
  
 L’avantage d’un code vérifiable est l’une des principales raisons pour lesquelles WPF s’appuie sur le cadre .NET. Dans la mesure où du code vérifiable est utilisé, la possibilité d'exploiter des failles éventuelles est considérablement réduite.  
  
### <a name="code-access-security"></a>Sécurité d'accès du code  
 Un ordinateur client expose une grande variété de ressources auxquelles une application managée peut avoir accès, notamment le système de fichiers, le Registre, les services d'impression, l'interface utilisateur, la réflexion et les variables d'environnement. Avant qu’une application gérée puisse accéder à l’une des ressources d’une machine cliente, elle doit avoir la permission de .NET Framework pour le faire. Une autorisation dans le CAS <xref:System.Security.CodeAccessPermission>est une sous-classe de la ; Cas met en œuvre une sous-classe pour chaque ressource à laquelle les applications gérées peuvent y accéder.  
  
 L’ensemble des autorisations qu’une demande gérée est accordée par le TAS lorsqu’elle commence à exécuter est connu sous le nom d’ensemble d’autorisation et est déterminé par les éléments de preuve fournis par la demande. Pour les demandes WPF, la preuve fournie est l’emplacement, ou la zone, à partir de laquelle les applications sont lancées. Le TAS identifie les zones suivantes :  
  
- **Mon ordinateur**. applications lancées à partir de l'ordinateur client (entièrement fiable).  
  
- **Intranet local** : applications lancées à partir de l'intranet (niveau de confiance moyen).  
  
- **Internet**. applications lancées à partir d'Internet (niveau de confiance le plus faible).  
  
- **Sites de confiance**. applications identifiées par un utilisateur comme dignes de confiance (niveau de confiance le plus faible).  
  
- **Sites non fiables** : applications identifiées par un utilisateur comme étant non fiables (non approuvé).  
  
 Pour chacune de ces zones, le TAS fournit un ensemble d’autorisation prédéfini qui comprend les autorisations qui correspondent au niveau de confiance associé à chacune. notamment :  
  
- **FullTrust** : Pour les applications lancées à partir de la zone **My Computer.** Toutes les autorisations possibles sont accordées.  
  
- **LocalIntranet**. Pour les applications lancées à partir de la zone **Intranet locale.** Un sous-ensemble d'autorisations est accordé pour fournir un accès modéré aux ressources d'un ordinateur client : emplacement de stockage isolé, accès illimité à l'interface utilisateur, accès illimité aux boîtes de dialogue de fichier, réflexion limitée et accès limité aux variables d'environnement. Les autorisations permettant d'accéder aux ressources critiques comme le Registre ne sont pas fournies.  
  
- **Internet**. Pour les applications lancées à partir **d’Internet** ou **de sites de confiance.** Un sous-ensemble d'autorisations est accordé pour octroyer un accès limité aux ressources d'un ordinateur client : emplacement de stockage isolé, ouverture des fichiers uniquement et interface utilisateur limitée. Essentiellement, cet ensemble d’autorisation isole les applications de la machine cliente.  
  
 Les demandes identifiées comme provenant de la zone **des sites non fiables** n’obtiennent aucune autorisation du TAS. Par conséquent, il n'existe pas de jeu d'autorisations prédéfini pour ces applications.  
  
 Le chiffre suivant illustre la relation entre les zones, les ensembles d’autorisations, les autorisations et les ressources :  
  
 ![Diagramme qui affiche les ensembles d’autorisation de cas.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Les restrictions du bac à sable de sécurité de la zone Internet s’appliquent également à tout code qu’un XBAP importe à partir d’une bibliothèque système, y compris WPF. Cela garantit que chaque bit du code est verrouillé, même WPF. Malheureusement, pour être en mesure d’exécuter, un XBAP doit exécuter des fonctionnalités qui nécessitent plus d’autorisations que celles activées par le bac à sable de sécurité de la zone Internet.  
  
 Considérez une application XBAP qui comprend la page suivante :  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Pour exécuter ce XBAP, le code WPF sous-jacent doit exécuter plus de fonctionnalités que ce qui est disponible pour l’appel XBAP, y compris:  
  
- Création d’une poignée de fenêtre (HWND) pour le rendu  
  
- distribution de messages ;  
  
- chargement de la police Tahoma.  
  
 Du point de vue de la sécurité, il serait catastrophique d'autoriser l'application sandbox à accéder directement à l'une de ces opérations.  
  
 Heureusement, WPF s’occupe de cette situation en permettant à ces opérations d’exécuter avec des privilèges élevés au nom de l’application bacée à sable. Bien que toutes les opérations WPF soient vérifiées par rapport aux autorisations de sécurité limitées de la zone Internet du domaine d’application du XBAP, WPF (comme avec d’autres bibliothèques système) reçoit un ensemble d’autorisation qui inclut toutes les autorisations possibles.
  
 Cela exige que WPF reçoive des privilèges élevés tout en empêchant ces privilèges d’être régis par l’ensemble d’autorisation de zone Internet du domaine de l’application hôte.  
  
 WPF le fait en utilisant la méthode **Assert** d’une autorisation. Le code suivant en donne l'illustration.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **L’Assert** empêche essentiellement les autorisations illimitées exigées par WPF d’être limitées par les autorisations de zone Internet du XBAP.  
  
 Du point de vue de la plate-forme, WPF est responsable de l’utilisation **correcte d’Assert** ; une utilisation incorrecte **d’Assert** pourrait permettre au code malveillant d’élever les privilèges. Par conséquent, il est alors important d’appeler **Assert** uniquement en cas de besoin, et de s’assurer que les restrictions des bacs à sable restent intactes. Par exemple, le code en mode sandbox n'est pas autorisé à ouvrir des fichiers aléatoires, mais il est autorisé à utiliser des polices. WPF permet aux applications sandboxed d’utiliser la fonctionnalité de police en appelant **Assert**, et pour WPF de lire des fichiers connus pour contenir ces polices pour le compte de l’application bacée à sable.  
  
### <a name="clickonce-deployment"></a>Déploiement ClickOnce  
 ClickOnce est une technologie de déploiement complète qui est incluse avec .NET Framework, et s’intègre avec Visual Studio (voir [la sécurité ClickOnce et le déploiement](/visualstudio/deployment/clickonce-security-and-deployment) pour des informations détaillées). Les applications WPF autonomes peuvent être déployées à l’aide de ClickOnce, tandis que les applications hébergées par navigateur doivent être déployées avec ClickOnce.  
  
 Les applications déployées à l’aide de ClickOnce reçoivent une couche de sécurité supplémentaire sur la sécurité d’accès au code (CAS); essentiellement, clickOnce demandes déployées demandent les autorisations dont ils ont besoin. Seules ces autorisations leur sont accordées si elles ne dépassent pas le jeu d'autorisations pour la zone à partir de laquelle l'application est déployée. En réduisant l’ensemble des autorisations à uniquement ceux qui sont nécessaires, même si elles sont inférieures à celles fournies par l’ensemble d’autorisation de la zone de lancement, le nombre de ressources auxquelles l’application a accès est réduit à un strict minimum. Par conséquent, si l'application est détournée, les risques de dommages sur l'ordinateur client sont réduits.  
  
### <a name="security-critical-methodology"></a>Méthodologie critique de sécurité  
 Le code WPF qui utilise les autorisations pour activer le bac à sable de la zone Internet pour les applications XBAP doit être maintenu au plus haut degré possible d’audit et de contrôle de sécurité. Pour faciliter cette exigence, .NET Framework fournit un nouveau soutien à la gestion du code qui augmente le privilège. Plus précisément, le CLR vous permet d’identifier le <xref:System.Security.SecurityCriticalAttribute>code qui élève le privilège et le marquer avec le ; tout code non <xref:System.Security.SecurityCriticalAttribute> marqué par devient *transparent* à l’aide de cette méthodologie. Inversement, le code managé qui n'est pas marqué avec <xref:System.Security.SecurityCriticalAttribute> est empêché d'élever le privilège.  
  
 La méthodologie de sécurité critique permet l’organisation du code WPF qui élève le privilège dans le *noyau critique de sécurité*, le reste étant transparent. L’isolement du code essentiel à la sécurité permet à l’équipe d’ingénierie du WPF de concentrer une analyse de sécurité et un contrôle de source supplémentaires sur le noyau critique de sécurité au-delà des pratiques de sécurité standard (voir [WPF Security Strategy - Security Engineering](wpf-security-strategy-security-engineering.md)).  
  
 Notez que .NET Framework permet au code de confiance d’étendre le bac à <xref:System.Security.AllowPartiallyTrustedCallersAttribute> sable de la zone Internet XBAP en permettant aux développeurs d’écrire des assemblages gérés marqués par (APTCA) et déployés dans le Global Assembly Cache (GAC) de l’utilisateur. Marquer un assembly avec APTCA est une opération de sécurité très sensible, car n'importe quel code peut appeler cet assembly, y compris du code malveillant en provenance d'Internet. Cette opération exige la plus grande prudence et le respect des meilleures pratiques. De plus, les utilisateurs doivent décider d'approuver ce logiciel pour pouvoir l'installer.  
  
## <a name="microsoft-internet-explorer-security"></a>Sécurité de Microsoft Internet Explorer  
 Au-delà de la réduction des problèmes de sécurité et de la simplification de la configuration de sécurité, Microsoft Internet Explorer 6 (SP2) contient plusieurs fonctionnalités qui améliorent la sécurité des utilisateurs d’applications de navigateur XAML (XBAP). L'idée-force de ces fonctionnalités est d'offrir aux utilisateurs un contrôle accru sur leur navigation.  
  
 Avant IE6 SP2, les utilisateurs pouvaient être soumis à l’un des éléments suivants :  
  
- affichage de fenêtres intempestives aléatoires ;  
  
- redirection de script confuse ;  
  
- nombreuses boîtes de dialogue de sécurité sur certains sites web.  
  
 Dans certains cas, des sites Web peu fiables tenteraient [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] de tromper les utilisateurs en usurpant l’installation ou en montrant à plusieurs reprises une boîte de dialogue d’installation Microsoft ActiveX, même si l’utilisateur peut l’avoir annulée. Il possible que ces techniques aient amené un nombre significatif d'utilisateurs à prendre de mauvaises décisions aboutissant à l'installation de logiciels espions.  
  
 IE6 SP2 comprend plusieurs fonctionnalités pour atténuer ce type de problèmes, qui tournent autour du concept d’initiation des utilisateurs. IE6 SP2 détecte quand un utilisateur a cliqué sur un lien ou un élément de page avant une action, qui est connu sous le nom *d’initiation de l’utilisateur*, et le traite différemment que lorsqu’une action similaire est plutôt déclenchée par le script sur une page. À titre d’exemple, IE6 SP2 intègre un **bloqueur pop-up** qui détecte lorsqu’un utilisateur clique sur un bouton avant la création de la page. Cela permet à IE6 SP2 de permettre la plupart des pop-ups inoffensifs tout en empêchant les pop-ups que les utilisateurs ne demandent ni ne veulent. Les pop-ups bloqués sont piégés sous la nouvelle **barre d’information**, ce qui permet à l’utilisateur de remplacer manuellement le bloc et de voir le pop-up.  
  
 La même logique d’initiation utilisateur est également appliquée aux invites de sécurité **Open**/**Save.** Les boîtes de dialogue d’installation ActiveX sont toujours piégées sous la barre d’information à moins qu’elles ne représentent une mise à niveau à partir d’un contrôle précédemment installé. Ces mesures se combinent pour donner à l'utilisateur une expérience plus sûre et mieux contrôlée, puisqu'ils sont protégés contre les sites qui les poussent à installer des logiciels indésirables ou malveillants.  
  
 Ces fonctionnalités protègent également les clients qui utilisent IE6 SP2 pour naviguer vers des sites Web qui leur permettent de télécharger et d’installer des applications WPF. En particulier, c’est parce que IE6 SP2 offre une meilleure expérience utilisateur qui réduit les chances pour les utilisateurs d’installer des applications malveillantes ou sournoises indépendamment de ce que la technologie a été utilisée pour le construire, y compris WPF. WPF ajoute à ces protections en utilisant ClickOnce pour faciliter le téléchargement de ses applications sur Internet. Étant donné que les applications de navigateur XAML (XBAP) s’exécutent dans un bac à sable de sécurité de zone Internet, elles peuvent être lancées de manière transparente. D’autre part, les applications WPF autonomes exigent une pleine confiance pour exécuter. Pour ces applications, ClickOnce affichera une boîte de dialogue de sécurité pendant le processus de lancement afin d’aviser l’utilisation des exigences de sécurité supplémentaires de l’application. Cependant, cette opération nécessite également l'intervention de l'utilisateur et peut être annulée.  
  
 Internet Explorer 7 intègre et étend les capacités de sécurité de iE6 SP2 dans le cadre d’un engagement continu en matière de sécurité.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité d’accès au code](../misc/code-access-security.md)
- [Sécurité](security-wpf.md)
- [Sécurité de confiance partielle WPF](wpf-partial-trust-security.md)
- [Stratégie de sécurité de WPF - ingénierie de sécurité](wpf-security-strategy-security-engineering.md)
