---
title: Temps de démarrage d'une application
ms.date: 03/30/2017
helpviewer_keywords:
- splash screen [WPF], startup time
- WPF [WPF], startup time
- startup time [WPF]
- application startup [WPF]
- performance [WPF], startup time
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
ms.openlocfilehash: 0fae3ac1769163101dcdb183f4c5c2135354b1fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145421"
---
# <a name="application-startup-time"></a>Temps de démarrage d'une application
La quantité de temps nécessaire pour démarrer une application WPF peut varier considérablement. Cette rubrique décrit les différentes techniques permettant de réduire le temps de démarrage (perçu et réel) pour une application Windows Presentation Foundation (WPF).  
  
## <a name="understanding-cold-startup-and-warm-startup"></a>Présentation de démarrage à froid et du démarrage à chaud  
 Le démarrage à froid se produit lorsque votre application démarre pour la première fois après un redémarrage du système, ou lorsque vous démarrez votre application, la fermez, puis la démarrez à nouveau après un certain temps. Lorsqu’une application démarre, si les pages requises (code, données statiques, registre, etc.) ne sont pas présentes dans la liste d’attente du Gestionnaire de mémoire Windows, des défauts de page se produisent. L’accès au disque est requis pour mettre les pages en mémoire.  
  
 Le démarrage à chaud se produit lorsque la plupart des pages pour les principaux composants du common language runtime (CLR) sont déjà chargés en mémoire, ce qui réduit le temps d’accès disque coûteux. C’est pourquoi une application managée démarre plus vite lorsqu’elle s’exécute une deuxième fois.  
  
## <a name="implement-a-splash-screen"></a>Implémentation d’un écran de démarrage  
 Dans les cas où il y a un délai notable et inévitable entre le démarrage d’une application et l’affichage de la première interface utilisateur, optimisez le temps de démarrage perçu à l’aide un *écran de démarrage*. Cette approche affiche une image presque immédiatement après que l’utilisateur démarre l’application. Lorsque l’application est prête à afficher sa première interface utilisateur, l’écran de démarrage disparaît en fondu. En commençant par le .NET Framework 3.5 <xref:System.Windows.SplashScreen> SP1, vous pouvez utiliser la classe pour implémenter un écran d’éclaboussure. Pour plus d’informations, consultez [Ajouter un écran de démarrage dans une application WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
 Vous pouvez également implémenter votre propre écran de démarrage à l’aide des graphiques Win32 natifs. Affichez votre <xref:System.Windows.Application.Run%2A> implémentation avant que la méthode ne soit appelée.  
  
## <a name="analyze-the-startup-code"></a>Analyse du code de démarrage  
 Déterminez la raison pour un démarrage à froid lent. Les E/S du disque peuvent être en cause, mais cela n’est pas toujours le cas. En général, vous devez réduire l’utilisation des ressources externes, comme le réseau, les services web ou le disque.  
  
 Avant de tester, vérifiez qu’il n’y pas d’autres applications ou services utilisant du code managé ou WPF.  
  
 Démarrez votre application WPF immédiatement après un redémarrage et déterminez la durée avant affichage. Si tous les lancements suivants de votre application (démarrage à chaud) sont beaucoup plus rapides, le problème du démarrage à froid est probablement causé par les E/S.  
  
 Si le problème de démarrage à froid de votre application n’est pas lié aux E/S, il est probable que votre application effectue une initialisation ou un calcul de longue durée, attende qu’un événement se termine ou nécessite beaucoup de compilation JIT au démarrage. Les sections suivantes décrivent certaines de ces situations plus en détail.  
  
## <a name="optimize-module-loading"></a>Optimisation du chargement des modules  
 Utilisez des outils tels que Process Explorer (Procexp.exe) et Tlist.exe pour déterminer les modules que votre application charge. La commande `Tlist <pid>` montre tous les modules chargés par un processus.  
  
 Par exemple, si vous n’êtes pas connecté à Internet et que vous voyez que System.Web.dll est chargé, il existe un module dans votre application qui fait référence à cet assembly. Vérifiez que la référence est nécessaire.  
  
 Si votre application comporte plusieurs modules, fusionnez-les en un seul module. Cette approche nécessite moins de surcharge de chargement d’assemblys CLR. Avoir moins d’assemblys signifie également que le CLR a moins d’états à maintenir.  
  
## <a name="defer-initialization-operations"></a>Report des opérations d’initialisation  
 Envisagez de différer le code d’initialisation jusqu'au rendu de la fenêtre principale de l’application.  
  
 N’oubliez pas que l’initialisation peut être effectuée à l’intérieur d’un constructeur de classe, et que si le code d’initialisation référence d’autres classes, cela peut provoquer un effet de cascade dans lequel de nombreux constructeurs de classe sont exécutés.  
  
## <a name="avoid-application-configuration"></a>Éviter la configuration d'application  
 Envisagez d’éviter la configuration de l’application. Par exemple, si une application a des exigences de configuration simples et des objectifs de temps de démarrage stricts, des entrées de registre ou un fichier INI simple peuvent être une alternative de démarrage plus rapide.  
  
## <a name="utilize-the-gac"></a>Utiliser le GAC  
 Si un assembly n’est pas installé dans le Global Assembly Cache (GAC), des retards sont causés par la vérification du hachage des assemblys avec nom fort et la validation des images Ngen si une image native de cet assembly est disponible sur l’ordinateur. La vérification des noms forts est ignorée pour tous les assemblys installés dans le GAC. Pour plus d'informations, consultez [Gacutil.exe (Global Assembly Cache Tool)](../../tools/gacutil-exe-gac-tool.md).  
  
## <a name="use-ngenexe"></a>Utiliser Ngen.exe  
 Envisagez d’utiliser Native Image Generator (Ngen.exe) sur votre application. L’utilisation de Ngen.exe signifie que vous remplacez une partie de la consommation d’UC par plus d’accès au disque, car l’image native générée par Ngen.exe est susceptible d’être plus grande que l’image MSIL.  
  
 Pour améliorer le temps de démarrage à chaud, vous devez toujours utiliser Ngen.exe sur votre application, car cela vous fait économiser le coût de la compilation JIT du code d’application par l’UC.  
  
 Dans certains scénarios de démarrage à froid, Ngen.exe peut également s’avérer utile. En effet, le compilateur JIT (mscorjit.dll) ne devra pas être chargé dans ce cas.  
  
 La présence à la fois de modules Ngen et JIT peut avoir le pire effet. En effet, mscorjit.dll doit être chargé, et lorsque le compilateur JIT travaille sur votre code, l’accès à de nombreuses pages dans les images Ngen est nécessaire lorsque le compilateur JIT lit les métadonnées des assemblys.  
  
### <a name="ngen-and-clickonce"></a>ClickOnce et Ngen  
 La façon dont vous prévoyez de déployer votre application peut également faire une différence dans le temps de chargement. Le déploiement de l’application ClickOnce ne prend pas en charge Ngen. Si vous décidez d’utiliser Ngen.exe pour votre application, vous devez utiliser un autre mécanisme de déploiement, comme Windows Installer.  
  
 Pour plus d’informations, consultez [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).  
  
### <a name="rebasing-and-dll-address-collisions"></a>Relocalisation et collisions d’adresses DLL  
 Si vous utilisez Ngen.exe, sachez que la relocalisation peut se produire lorsque des images natives sont chargées en mémoire. Si une DLL n’est pas chargée à son adresse de base préférée car cette plage d’adresses est déjà allouée, le chargeur Windows la chargera à une autre adresse, ce qui peut prendre beaucoup de temps.  
  
 Vous pouvez utiliser l’outil Virtual Address Dump (Vadump.exe) pour vérifier s’il existe des modules dans lesquels toutes les pages sont privées. Si c’est le cas, le module a peut-être été relocalisé à une adresse différente. Par conséquent, ses pages ne peuvent pas être partagées.  
  
 Pour plus d’informations sur la définition de l’adresse de base, consultez [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).  
  
## <a name="optimize-authenticode"></a>Optimiser Authenticode  
 La vérification Authenticode ajoute au temps de démarrage. Les assemblys signés par Authenticode doivent être vérifiés avec l’autorité de certification (CA). Cette vérification peut prendre du temps, car elle peut requérir la connexion au réseau à plusieurs reprises pour télécharger les listes de révocation de certificats actuelles. Cela garantit également qu’il existe une chaîne complète de certificats valides sur le chemin d’accès à une racine approuvée. Cela peut se traduire par plusieurs secondes de délai lors du chargement de l’assembly.  
  
 Envisagez d’installer le certificat d’autorité de certification sur l’ordinateur client, ou évitez d’utiliser Authenticode lorsque c’est possible. Si vous savez que votre application ne nécessite pas de preuve de l’éditeur, vous n’avez pas à payer le coût de la vérification de la signature.  
  
 À partir de .NET Framework 3.5, il existe une option de configuration qui permet de contourner la vérification Authenticode. Pour ce faire, ajoutez le paramètre suivant au fichier app.exe.config :  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>
    </runtime>  
</configuration>  
```  
  
 Pour plus d’informations, voir [ \<générerPublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md).  
  
## <a name="compare-performance-on-windows-vista"></a>Comparaison des performances sur Windows Vista  
 Le gestionnaire de mémoire dans Windows Vista possède une technologie appelée SuperFetch. SuperFetch analyse les modèles d’utilisation de la mémoire au fil du temps pour déterminer le contenu de mémoire optimal pour un utilisateur spécifique. Il fonctionne en continu pour conserver ce contenu à tout moment.  
  
 Cette approche diffère de la technique de prérécupération utilisée dans Windows XP, qui précharge les données en mémoire sans analyser les modèles d’utilisation. Au fil du temps, si l’utilisateur utilise fréquemment votre application WPF sur Windows Vista, le temps de démarrage à froid de votre application peut s’améliorer.  
  
## <a name="use-appdomains-efficiently"></a>Utiliser efficacement les AppDomains  
 Si possible, chargez les assemblys dans une zone de code indépendante du domaine pour vous assurer que l’image native, s’il en existe une, est utilisée dans tous les AppDomains créés dans l’application.  
  
 Pour des performances optimales, appliquez une communication interdomaine efficace en réduisant les appels interdomaines. Si possible, utilisez des appels sans arguments ou avec des arguments de type primitif.  
  
## <a name="use-the-neutralresourceslanguage-attribute"></a>Utilisation de l’attribut NeutralResourcesLanguage  
 Utilisez <xref:System.Resources.NeutralResourcesLanguageAttribute> le pour spécifier la culture neutre pour le <xref:System.Resources.ResourceManager>. Cette approche évite les échecs de recherche d’assembly.  
  
## <a name="use-the-binaryformatter-class-for-serialization"></a>Utilisation de la classe BinaryFormatter pour la sérialisation  
 Si vous devez utiliser la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sérialisation, utilisez la classe au lieu de la <xref:System.Xml.Serialization.XmlSerializer> classe. La <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> classe est mise en œuvre dans la Bibliothèque de classe de base (BCL) dans l’assemblage mscorlib.dll. Le <xref:System.Xml.Serialization.XmlSerializer> est implémenté dans l’assemblage System.Xml.dll, qui pourrait être un DLL supplémentaire à charger.  
  
 Si vous devez <xref:System.Xml.Serialization.XmlSerializer> utiliser la classe, vous pouvez obtenir de meilleures performances si vous pré-générer l’assemblage de sérialisation.  
  
## <a name="configure-clickonce-to-check-for-updates-after-startup"></a>Configuration de ClickOnce pour vérifier les mises à jour après le démarrage  
 Si votre application utilise ClickOnce, évitez l’accès au réseau sur le démarrage en configurant ClickOnce pour vérifier le site de déploiement pour les mises à jour après le début de l’application.  
  
 Si vous utilisez le modèle d’application de navigateur XAML (XBAP), gardez à l’esprit que ClickOnce vérifie le site de déploiement pour les mises à jour, même si le XBAP est déjà dans le cache ClickOnce. Pour plus d'informations, consultez [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).  
  
## <a name="configure-the-presentationfontcache-service-to-start-automatically"></a>Configuration du service PresentationFontCache pour qu’il démarre automatiquement  
 La première application WPF qui s’exécute après un redémarrage est le service PresentationFontCache. Le service met en cache les polices système améliore l’accès aux polices et augmente les performances globales. Il existe une surcharge du démarrage du service, et dans certains environnements contrôlés, envisagez de configurer le service pour démarrer automatiquement lors du redémarrage du système.  
  
## <a name="set-data-binding-programmatically"></a>Définition des données de liaison par programmation  
 Au lieu d’utiliser XAML pour définir le <xref:System.Windows.FrameworkElement.DataContext%2A> déclarativement pour la <xref:System.Windows.Application.OnActivated%2A> fenêtre principale, envisager de le définir programmatiquement dans la méthode.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.SplashScreen>
- <xref:System.AppDomain>
- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- <xref:System.Resources.ResourceManager>
- [Ajouter un écran de démarrage dans une application WPF](../app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)
- [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md)
- [\<générerPublisherEvidence> Element](../../configure-apps/file-schema/runtime/generatepublisherevidence-element.md)
