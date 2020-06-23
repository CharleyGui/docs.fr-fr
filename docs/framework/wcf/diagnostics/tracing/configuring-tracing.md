---
title: Configuration du traçage
description: Découvrez comment activer le traçage, configurer des sources de suivi, définir le suivi et la propagation d’activité, et définir des écouteurs de suivi pour accéder aux suivis dans WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 55d701ee6769099698d2fd869a1502d94237b5a8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245347"
---
# <a name="configuring-tracing"></a>Configuration du traçage
Cette rubrique décrit comment activer le suivi, configurer des sources de suivi pour émettre des suivis et définir des niveaux de suivi, définir le suivi et la propagation d'activité afin de prendre en charge la corrélation de suivi de bout en bout, et définir des écouteurs de suivi pour accéder aux suivis.  
  
 Pour obtenir des recommandations sur les paramètres de suivi dans un environnement de production ou de débogage, consultez [paramètres recommandés pour le suivi et la journalisation des messages](recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
> Sur Windows 8 vous devez exécuter votre application avec élévation de privilèges (Exécuter en tant qu'administrateur) pour que votre application génère des journaux de traces.  
  
## <a name="enabling-tracing"></a>Activation du traçage  
 Windows Communication Foundation (WCF) génère les données suivantes pour le suivi de diagnostic :  
  
- Suivi des jalons de processus dans tous les composants des applications, tels que les appels d’opération, les exceptions de code, les avertissements et d’autres événements de traitement significatifs.  
  
- Événements d’erreur Windows en cas de dysfonctionnement de la fonctionnalité de suivi. Consultez [journalisation des événements](../event-logging/index.md).  
  
 Le suivi WCF repose sur <xref:System.Diagnostics> . Pour utiliser le traçage, vous devez définir des sources de trace dans le fichier de configuration ou dans le code. WCF définit une source de suivi pour chaque assembly WCF. La `System.ServiceModel` source de suivi est la source de suivi WCF la plus générale et enregistre les étapes majeures de traitement dans la pile de communication WCF, de l’entrée/sortie du transport à l’entrée/sortie du code utilisateur. La source de suivi `System.ServiceModel.MessageLogging` enregistre tous les messages qui circulent dans le système.  
  
 Le suivi est désactivé par défaut. Pour activer le suivi, vous devez créer un écouteur de suivi et définir un niveau de suivi autre que « désactivé » pour la source de suivi sélectionnée dans la configuration ; dans le cas contraire, WCF ne génère pas de traces. Si vous ne spécifiez pas d'écouteur, le suivi est automatiquement désactivé. Si un écouteur est défini mais qu'aucun niveau n'est spécifié, le niveau a la valeur « Désactivé » par défaut, ce qui signifie qu'aucun suivi n'est émis.  
  
 Si vous utilisez des points d’extensibilité WCF tels que des appelants d’opérations personnalisées, vous devez émettre vos propres suivis. En effet, si vous implémentez un point d’extensibilité, WCF ne peut plus émettre les traces standard dans le chemin d’accès par défaut. Si vous n'implémentez par la prise en charge du suivi manuel à l'aide de l'émission de suivis, les suivis peuvent ne pas s'afficher comme prévu.  
  
 Vous pouvez configurer le suivi en modifiant le fichier de configuration de l’application, soit Web.config pour les applications hébergées sur le Web, soit Appname.exe.config pour les applications auto-hébergées. Vous trouverez ci-dessous un exemple de ce type de modification : Pour plus d’informations sur ces paramètres, consultez la section « Configuration des écouteurs de suivi pour consommer des traces ».  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
> Pour modifier le fichier de configuration d’un projet de service WCF dans Visual Studio, cliquez avec le bouton droit sur le fichier de configuration de l’application : Web.config pour les applications hébergées sur le Web ou Appname.exe.config pour une application auto-hébergée dans **Explorateur de solutions**. Choisissez ensuite l’élément de menu contextuel **modifier la configuration WCF** . Cela lance l' [outil Éditeur de configuration (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md), qui vous permet de modifier les paramètres de configuration des services WCF à l’aide d’une interface utilisateur graphique.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Configuration de sources de suivi de façon à émettre des suivis  
 WCF définit une source de suivi pour chaque assembly. Les écouteurs définis pour cette source accèdent aux suivis générés dans un assembly. Les sources de suivi suivantes sont définies :  
  
- System. ServiceModel : journalise toutes les étapes du traitement WCF, chaque fois que la configuration est lue, un message est traité dans le transport, le traitement de sécurité, un message est distribué dans le code utilisateur, et ainsi de suite.  
  
- System.ServiceModel.MessageLogging : enregistre tous les messages qui circulent dans le système.  
  
- System.IdentityModel.  
  
- System.ServiceModel.Activation.  
  
- System.IO.Log : enregistrement pour l'interface .NET Framework dans le système CLFS (Common Log File System).  
  
- System.Runtime.Serialization : enregistre la lecture ou l'écriture des objets.  
  
- CardSpace.  
  
 Vous pouvez configurer chaque source de suivi de façon à utiliser le même écouteur (partagé), comme indiqué dans l'exemple de configuration suivant :  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 De plus, vous pouvez ajouter des sources de suivi définies par l'utilisateur, comme illustré par l'exemple suivant, de façon à émettre des suivis de code utilisateur :  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />
</system.diagnostics>  
```  
  
 Pour plus d’informations sur la création de sources de suivi définies par l’utilisateur, consultez [extension du suivi](../../samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Configuration d'écouteurs de suivi pour consommer des suivis  
 Lors de l’exécution, WCF alimente les données de trace aux écouteurs, qui traitent les données. WCF fournit plusieurs écouteurs prédéfinis pour <xref:System.Diagnostics> , qui diffèrent au format utilisé pour la sortie. Vous pouvez également ajouter des types d'écouteurs personnalisés.  
  
 Vous pouvez utiliser `add` pour indiquer les nom et type de l'écouteur de suivi à utiliser. Dans notre exemple de configuration, nous avons nommé l'écouteur `traceListener` et ajouté l'écouteur de suivi standard .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) comme type à utiliser. Vous pouvez ajouter un nombre quelconque d'écouteurs de suivi pour chaque source. Si l'écouteur de suivi émet le suivi dans un fichier, vous devez spécifier le nom et l'emplacement du fichier de sortie dans le fichier de configuration. Pour cela, vous devez affecter à `initializeData` le nom du fichier pour cet écouteur. Si vous ne spécifiez pas de nom de fichier, un nom de fichier aléatoire est généré en fonction du type d'écouteur utilisé. Si <xref:System.Diagnostics.XmlWriterTraceListener> est utilisé, un nom de fichier sans extension est généré. Si vous implémentez un écouteur personnalisé, vous pouvez également utiliser cet attribut pour recevoir des données d'initialisation autres qu'un nom de fichier. Par exemple, vous pouvez spécifier un identificateur de base de données pour cet attribut.  
  
 Vous pouvez configurer un écouteur de suivi personnalisé pour envoyer des suivis sur le câble, par exemple à une base de données distante. En tant que responsable du déploiement d'applications, vous devez appliquer un contrôle d'accès approprié sur les journaux de suivi sur l'ordinateur distant.  
  
 Vous pouvez également configurer un écouteur de suivi par programmation. Pour plus d’informations, consultez [Comment : créer et initialiser des écouteurs de suivi](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) et [créer un TraceListener personnalisé](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).  
  
> [!CAUTION]
> `System.Diagnostics.XmlWriterTraceListener` n'étant pas thread-safe, la source de suivi peut verrouiller des ressources exclusivement lors de la sortie de suivis. Lorsque de nombreux threads sortent des suivis vers une source de suivi configurée pour utiliser cet écouteur, un conflit de ressource peut se produire, provoquant une dégradation significative des performances. Pour résoudre ce problème, vous devez implémenter un écouteur personnalisé thread-safe.  
  
## <a name="trace-level"></a>Niveau de suivi  
 Le niveau de suivi est contrôlé par le paramètre `switchValue` de la source de suivi. Les niveaux de suivi disponibles sont décrits dans le tableau suivant.  
  
|Niveau de suivi|Nature des événements suivis|Contenu des événements suivis|Événements suivis|Cible utilisateur|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Désactivé|N/A|N/A|Aucun suivi n'est émis.|N/A|  
|Critique|Événements « négatifs » : événements qui indiquent un traitement inattendu ou une condition d’erreur.||Les exceptions non prises en charge, notamment les suivantes, sont enregistrées :<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (le CLR appelle tout ThreadAbortExceptionHandler)<br />-StackOverflowException (ne peut pas être intercepté)<br />-ConfigurationErrorsException<br />-SEHException<br />-Erreurs de démarrage de l’application<br />-Événements FailFast<br />-Blocage du système<br />-Messages incohérents : suivis des messages qui provoquent l’échec de l’application.|Administrateurs<br /><br /> Développeurs d’applications|  
|Erreur|Événements « négatifs » : événements qui indiquent un traitement inattendu ou une condition d’erreur.|Un traitement inattendu s'est produit. L’application n’a pas pu effectuer une tâche comme prévu. Toutefois, l'application s'exécute encore.|Toutes les exceptions sont enregistrées.|Administrateurs<br /><br /> Développeurs d’applications|  
|Avertissement|Événements « négatifs » : événements qui indiquent un traitement inattendu ou une condition d’erreur.|Un problème possible s'est produit ou peut se produire, mais l'application fonctionne encore correctement. Toutefois, elle risque de ne plus fonctionner correctement.|-L’application reçoit davantage de demandes que ses paramètres de limitation autorisent.<br />-La file d’attente de réception est proche de sa capacité maximale configurée.<br />-Dépassement du délai d’attente.<br />-Les informations d’identification sont rejetées.|Administrateurs<br /><br /> Développeurs d’applications|  
|Information|Événements « positifs » : événements qui marquent des jalons réussis|Jalons importants et atteints relatifs à l'exécution d'application, indépendamment du fonctionnement correct de l'application.|En général, des messages d'aide au contrôle et au diagnostic de l'état système, à la mesure des performances ou au profilage sont générés. Vous pouvez utiliser ces informations pour la planification de capacité et la gestion des performances :<br /><br /> -Les canaux sont créés.<br />-Les écouteurs de point de terminaison sont créés.<br />-Le message entre/quitte le transport.<br />-Le jeton de sécurité est récupéré.<br />-Le paramètre de configuration est lu.|Administrateurs<br /><br /> Développeurs d’applications<br /><br /> Développeurs de produits.|  
|Commentaires|Événements « positifs » : événements qui marquent des jalons réussis.|Les événements de bas niveau pour le code utilisateur et la maintenance sont émis.|En général, vous pouvez utiliser ce niveau pour le débogage ou l'optimisation d'application.<br /><br /> -En-tête de message compris.|Administrateurs<br /><br /> Développeurs d’applications<br /><br /> Développeurs de produits.|  
|ActivityTracing||Transfert d'événements entre des activités de traitement et des composants.|Ce niveau permet aux administrateurs et aux développeurs de corréler des applications dans le même domaine d'application :<br /><br /> -Traces pour les limites d’activité, telles que Start/Stop.<br />-Suivis pour les transferts.|Tous|  
|Tous||L'application peut fonctionner correctement. Tous les événements sont émis.|Tous les événements précédents.|Tous|  
  
 Les niveaux compris entre Verbose et Critique sont empilés les uns sur les autres, autrement dit chaque niveau de suivi inclut tous les niveaux supérieurs hormis le niveau Désactivé. Par exemple, un écouteur qui écoute au niveau Avertissement reçoit les suivis des niveaux Critique, Erreur et Avertissement. Le niveau Tout inclut les événements du niveau Verbose au niveau Critique et les événements ActivityTracing.  
  
> [!CAUTION]
> Les niveaux Informations, Commentaires et ActivityTracing génèrent de nombreux suivis, ce qui peut avoir un impact négatif sur le débit des messages si vous avez utilisé toutes les ressources disponibles sur l'ordinateur.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Configuration du suivi d'activité et de la propagation pour la corrélation  
 La valeur `activityTracing` spécifiée pour l'attribut `switchValue` est utilisée pour activer le suivi d'activité, qui émet des suivis pour les transferts et limites d'activité dans les points de terminaison.  
  
> [!NOTE]
> Lorsque vous utilisez certaines fonctionnalités d’extensibilité dans WCF, vous pouvez obtenir un <xref:System.NullReferenceException> lorsque le suivi d’activité est activé. Pour résoudre ce problème, vérifiez le fichier de configuration de votre application et assurez-vous que l'attribut `switchValue` de votre source de suivi n'a pas la valeur `activityTracing`.  
  
 L'attribut `propagateActivity` indique si l'activité doit être propagée vers d'autres points de terminaison qui participent à l'échange de messages. En affectant à cet attribut la valeur `true`, vous pouvez prendre des fichiers de suivi générés par deux points de terminaison quelconque et observer comment un ensemble de suivis sur un point de terminaison a été transféré vers un ensemble de suivis sur un autre point de terminaison.  
  
 Pour plus d’informations sur le suivi et la propagation des activités, consultez [propagation](propagation.md).  
  
 `propagateActivity`Et les `ActivityTracing` valeurs booléennes s’appliquent à l’TraceSource System. ServiceModel. La `ActivityTracing` valeur s’applique également à toute source de suivi, y compris WCF ou défini par l’utilisateur.  
  
 Vous ne pouvez pas utiliser l'attribut `propagateActivity` avec des sources de suivi définies par l'utilisateur. Pour la propagation d'ID d'activité de code utilisateur, assurez-vous de ne pas définir ServiceModel `ActivityTracing`, tout en ayant encore l'attribut `propagateActivity` ServiceModel défini à `true`.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
- [Administration et diagnostics](../index.md)
- [Comment : créer et initialiser les écouteurs de la trace](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Création d'un TraceListener personnalisé](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
