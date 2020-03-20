---
title: Configuration du traçage
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: d8b216bf5497cf2a1faa2fa24ba1d8b3102f6f10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185740"
---
# <a name="configuring-tracing"></a>Configuration du traçage
Cette rubrique décrit comment activer le suivi, configurer des sources de suivi pour émettre des suivis et définir des niveaux de suivi, définir le suivi et la propagation d'activité afin de prendre en charge la corrélation de suivi de bout en bout, et définir des écouteurs de suivi pour accéder aux suivis.  
  
 Pour retracer les recommandations de paramètres dans l’environnement de production ou de débogage, consultez [les paramètres recommandés pour le traçage et l’enregistrement des messages.](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)  
  
> [!IMPORTANT]
> Sur Windows 8 vous devez exécuter votre application avec élévation de privilèges (Exécuter en tant qu'administrateur) pour que votre application génère des journaux de traces.  
  
## <a name="enabling-tracing"></a>Activation du traçage  
 Windows Communication Foundation (WCF) produit les données suivantes pour le suivi diagnostique :  
  
- Suivis des jalons de processus dans l'ensemble des composants des applications, tels que les appels d'opération, les exceptions de code, les avertissements et d'autres événements de traitement significatifs.  
  
- Événements d’erreur Windows en cas de dysfonctionnement de la fonctionnalité de suivi. Voir [l’enregistrement de l’événement](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 WCF traçage est <xref:System.Diagnostics>construit sur le dessus de . Pour utiliser le traçage, vous devez définir des sources de trace dans le fichier de configuration ou dans le code. WCF définit une source de traces pour chaque assemblage WCF. La `System.ServiceModel` source de traces est la source de trace WCF la plus générale, et les jalons de traitement des enregistrements à travers la pile de communication WCF, de l’entrée / laissant le transport à l’entrée / laisser le code utilisateur. La source de suivi `System.ServiceModel.MessageLogging` enregistre tous les messages qui circulent dans le système.  
  
 Le suivi est désactivé par défaut. Pour activer le traçage, vous devez créer un auditeur de traces et définir un niveau de trace autre que "Off" pour la source de trace sélectionnée en configuration; autrement, WCF ne génère aucune trace. Si vous ne spécifiez pas d'écouteur, le suivi est automatiquement désactivé. Si un écouteur est défini mais qu'aucun niveau n'est spécifié, le niveau a la valeur « Désactivé » par défaut, ce qui signifie qu'aucun suivi n'est émis.  
  
 Si vous utilisez des points d’extabilité WCF tels que les invocateurs d’opérations personnalisées, vous devez émettre vos propres traces. C’est parce que si vous implémentez un point d’extabilité, WCF ne peut plus émettre les traces standard dans le chemin par défaut. Si vous n'implémentez par la prise en charge du suivi manuel à l'aide de l'émission de suivis, les suivis peuvent ne pas s'afficher comme prévu.  
  
 Vous pouvez configurer le suivi en modifiant le fichier de configuration de l'application : Web.config pour les applications hébergées sur le Web, ou Appname.exe.config pour les applications auto-hébergées. Vous trouverez ci-dessous un exemple de ce type de modification : Pour plus d’informations sur ces paramètres, consultez la section « Configurer traces auditeurs pour consommer des traces ».  
  
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
> Pour modifier le fichier de configuration d’un projet de service WCF dans Visual Studio, cliquez à droite sur le fichier de configuration de l’application, soit Web.config pour les applications hébergées sur le Web, soit Appname.exe.config pour l’application auto-hébergée dans **Solution Explorer**. Choisissez ensuite l’élément de menu **contextuelle Edit WCF Configuration.** Cela lance [l’outil d’éditeur de configuration (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), qui vous permet de modifier les paramètres de configuration pour les services WCF à l’aide d’une interface utilisateur graphique.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Configuration de sources de suivi de façon à émettre des suivis  
 WCF définit une source de traces pour chaque assemblage. Les écouteurs définis pour cette source accèdent aux suivis générés dans un assembly. Les sources de suivi suivantes sont définies :  
  
- System.ServiceModel: Enregistre toutes les étapes du traitement WCF, chaque fois que la configuration est lue, un message est traité dans le transport, le traitement de sécurité, un message est envoyé dans le code utilisateur, et ainsi de suite.  
  
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
  
 Pour plus d’informations sur la création de sources de traces définies par l’utilisateur, voir [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Configuration d'écouteurs de suivi pour consommer des suivis  
 Au moment de l’exécution, WCF alimente les données de trace aux auditeurs qui traitent les données. WCF fournit plusieurs auditeurs <xref:System.Diagnostics>prédéfinis pour , qui diffèrent dans le format qu’ils utilisent pour la sortie. Vous pouvez également ajouter des types d'écouteurs personnalisés.  
  
 Vous pouvez utiliser `add` pour indiquer les nom et type de l'écouteur de suivi à utiliser. Dans notre exemple de configuration, nous avons nommé l'écouteur `traceListener` et ajouté l'écouteur de suivi standard .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) comme type à utiliser. Vous pouvez ajouter un nombre quelconque d'écouteurs de suivi pour chaque source. Si l'écouteur de suivi émet le suivi dans un fichier, vous devez spécifier le nom et l'emplacement du fichier de sortie dans le fichier de configuration. Pour cela, vous devez affecter à `initializeData` le nom du fichier pour cet écouteur. Si vous ne spécifiez pas de nom de fichier, un nom de fichier aléatoire est généré en fonction du type d'écouteur utilisé. Si <xref:System.Diagnostics.XmlWriterTraceListener> est utilisé, un nom de fichier sans extension est généré. Si vous implémentez un écouteur personnalisé, vous pouvez également utiliser cet attribut pour recevoir des données d'initialisation autres qu'un nom de fichier. Par exemple, vous pouvez spécifier un identificateur de base de données pour cet attribut.  
  
 Vous pouvez configurer un écouteur de suivi personnalisé pour envoyer des suivis sur le câble, par exemple à une base de données distante. En tant que responsable du déploiement d'applications, vous devez appliquer un contrôle d'accès approprié sur les journaux de suivi sur l'ordinateur distant.  
  
 Vous pouvez également configurer un écouteur de suivi par programmation. Pour plus d’informations, voir [Comment : Créer et initialiser les auditeurs de trace et](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) créer un [TraceListener personnalisé.](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)  
  
> [!CAUTION]
> `System.Diagnostics.XmlWriterTraceListener` n'étant pas thread-safe, la source de suivi peut verrouiller des ressources exclusivement lors de la sortie de suivis. Lorsque de nombreux threads sortent des suivis vers une source de suivi configurée pour utiliser cet écouteur, un conflit de ressource peut se produire, provoquant une dégradation significative des performances. Pour résoudre ce problème, vous devez implémenter un écouteur personnalisé thread-safe.  
  
## <a name="trace-level"></a>Niveau de suivi  
 Le niveau de suivi est contrôlé par le paramètre `switchValue` de la source de suivi. Les niveaux de suivi disponibles sont décrits dans le tableau suivant.  
  
|Niveau de suivi|Nature des événements suivis|Contenu des événements suivis|Événements suivis|Cible utilisateur|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|N/A|N/A|Aucun suivi n'est émis.|N/A|  
|Critique|Événements « négatifs » : événements indiquant un traitement inattendu ou une condition d’erreur.||Les exceptions non prises en charge, notamment les suivantes, sont enregistrées :<br /><br /> - OutOfMemoryException<br />- ThreadAbortException (le CLR invoque n’importe quel ThreadAbortExceptionHandler)<br />- StackOverflowException (ne peut pas être pris)<br />- ConfigurationErrorsException<br />- SEHException<br />- Erreurs de début d’application<br />- Événements failfast<br />- Le système est suspendu<br />- Messages empoisonnés : traces de messages qui font échouer l’application.|Administrateurs<br /><br /> Développeurs d’applications|  
|Error|Événements « négatifs » : événements indiquant un traitement inattendu ou une condition d’erreur.|Un traitement inattendu s'est produit. L’application n’a pas pu effectuer une tâche comme prévu. Toutefois, l'application s'exécute encore.|Toutes les exceptions sont enregistrées.|Administrateurs<br /><br /> Développeurs d’applications|  
|Avertissement|Événements « négatifs » : événements indiquant un traitement inattendu ou une condition d’erreur.|Un problème possible s'est produit ou peut se produire, mais l'application fonctionne encore correctement. Toutefois, elle risque de ne plus fonctionner correctement.|- L’application reçoit plus de demandes que ses paramètres de limitation ne le permettent.<br />- La file d’attente de réception est proche de sa capacité configurée maximale.<br />- Le délai d’attente a dépassé.<br />- Les titres de compétences sont rejetés.|Administrateurs<br /><br /> Développeurs d’applications|  
|Information|Événements « positifs » : des événements qui marquent des jalons réussis|Jalons importants et atteints relatifs à l'exécution d'application, indépendamment du fonctionnement correct de l'application.|En général, des messages d'aide au contrôle et au diagnostic de l'état système, à la mesure des performances ou au profilage sont générés. Vous pouvez utiliser ces informations pour la planification de capacité et la gestion des performances :<br /><br /> - Des canaux sont créés.<br />- Les auditeurs de point de terminaison sont créés.<br />- Message entre /feuilles de transport.<br />- Le jeton de sécurité est récupéré.<br />- Le réglage de configuration est lu.|Administrateurs<br /><br /> Développeurs d’applications<br /><br /> Développeurs de produits.|  
|Commentaires|Événements « positifs » : des événements qui marquent des jalons réussis.|Des événements de bas niveau pour le code utilisateur et la maintenance sont émis.|En général, vous pouvez utiliser ce niveau pour le débogage ou l'optimisation d'application.<br /><br /> - En-tête de message compris.|Administrateurs<br /><br /> Développeurs d’applications<br /><br /> Développeurs de produits.|  
|ActivityTracing||Transfert d'événements entre des activités de traitement et des composants.|Ce niveau permet aux administrateurs et aux développeurs de corréler des applications dans le même domaine d'application :<br /><br /> - Traces pour les limites d’activité, telles que le démarrage/arrêt.<br />- Traces pour les transferts.|Tous|  
|Tous||L'application peut fonctionner correctement. Tous les événements sont émis.|Tous les événements précédents.|Tous|  
  
 Les niveaux compris entre Verbose et Critique sont empilés les uns sur les autres, autrement dit chaque niveau de suivi inclut tous les niveaux supérieurs hormis le niveau Désactivé. Par exemple, un écouteur qui écoute au niveau Avertissement reçoit les suivis des niveaux Critique, Erreur et Avertissement. Le niveau Tout inclut les événements du niveau Verbose au niveau Critique et les événements ActivityTracing.  
  
> [!CAUTION]
> Les niveaux Informations, Commentaires et ActivityTracing génèrent de nombreux suivis, ce qui peut avoir un impact négatif sur le débit des messages si vous avez utilisé toutes les ressources disponibles sur l'ordinateur.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Configuration du suivi d'activité et de la propagation pour la corrélation  
 La valeur `activityTracing` spécifiée pour l'attribut `switchValue` est utilisée pour activer le suivi d'activité, qui émet des suivis pour les transferts et limites d'activité dans les points de terminaison.  
  
> [!NOTE]
> Lorsque vous utilisez certaines fonctionnalités d’extensibility <xref:System.NullReferenceException> dans WCF, vous pouvez obtenir un moment où le traçage de l’activité est activé. Pour résoudre ce problème, vérifiez le fichier de configuration de votre application et assurez-vous que l'attribut `switchValue` de votre source de suivi n'a pas la valeur `activityTracing`.  
  
 L'attribut `propagateActivity` indique si l'activité doit être propagée vers d'autres points de terminaison qui participent à l'échange de messages. En affectant à cet attribut la valeur `true`, vous pouvez prendre des fichiers de suivi générés par deux points de terminaison quelconque et observer comment un ensemble de suivis sur un point de terminaison a été transféré vers un ensemble de suivis sur un autre point de terminaison.  
  
 Pour plus d’informations sur le traçage et la propagation des activités, voir [Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Les `propagateActivity` `ActivityTracing` valeurs Boolean et Boolean s’appliquent à la TraceSource System.ServiceModel. La `ActivityTracing` valeur s’applique également à toute source de traces, y compris WCF ou définies par l’utilisateur.  
  
 Vous ne pouvez pas utiliser l'attribut `propagateActivity` avec des sources de suivi définies par l'utilisateur. Pour la propagation d'ID d'activité de code utilisateur, assurez-vous de ne pas définir ServiceModel `ActivityTracing`, tout en ayant encore l'attribut `propagateActivity` ServiceModel défini à `true`.  
  
## <a name="see-also"></a>Voir aussi

- [Traçage](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Comment : créer et initialiser les écouteurs de la trace](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Création d'un TraceListener personnalisé](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
