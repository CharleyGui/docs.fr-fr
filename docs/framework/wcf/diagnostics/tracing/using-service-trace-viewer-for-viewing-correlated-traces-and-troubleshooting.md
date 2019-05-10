---
title: Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: 8f51f49bf7346ea19e8f64b5ec537d36cce0d354
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662858"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes

Cette rubrique décrit le format des données de suivi, leur mode de consultation, et les approches qui utilisent Service Trace Viewer pour résoudre les problèmes posés par votre application.

## <a name="using-the-service-trace-viewer-tool"></a>Utilisation de l'outil Service Trace Viewer

L’outil Windows Communication Foundation (WCF) Service Trace Viewer vous permet de mettre en corrélation les traces de diagnostic produites par les écouteurs WCF pour localiser la cause racine d’une erreur. L’outil vous permet de facilement consulter, regrouper et filtrer des traces afin que vous pouvez diagnostiquer, réparer et vérifier les problèmes avec les services WCF. Pour plus d’informations sur l’utilisation de cet outil, consultez [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).

Cette rubrique contient des captures d’écran de suivis générés en exécutant la [Tracing and Message Logging](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemple, lorsqu’ils sont affichés à l’aide de la [outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Cette rubrique explique comment interpréter le contenu, les activités de suivi, et leur corrélation, et comment analyser un grand nombre de suivis au cours de la résolution des problèmes.

## <a name="viewing-trace-content"></a>Consultation du contenu de suivi

Un événement de suivi contient les informations significatives suivantes :

- Nom d'activité lorsqu'il est défini.

- Heure d'émission.

- Niveau de suivi.

- Nom de source de suivi.

- Nom du processus.

- ID de thread.

- Identificateur de suivi unique, qui est une URL qui pointe vers une destination dans Microsoft Docs, à partir de laquelle vous pouvez obtenir plus d’informations concernant le suivi.

 Tous ces éléments sont consultables dans le volet supérieur droit dans Service Trace Viewer, ou dans le **des informations de base** section dans la vue mise en forme du panneau inférieur droit lors de la sélection d’une trace.

> [!NOTE]
> Si le client et le service se trouvent sur le même ordinateur, les suivis des deux applications seront présents. Ils peuvent être filtrés à l’aide de la **nom de processus** colonne.

De plus, la vue mise en forme fournit également une description du suivi et des informations détaillées supplémentaires lorsqu'elles sont disponibles. Ces informations peuvent contenir le type d'exception et le message, les piles d'appel, l'action du message, les champs De/À, et d'autres informations sur les exceptions.

Dans la vue XML, les balises xml utiles incluent les éléments suivants :

- `<SubType>` (niveau de trace).

- `<TimeCreated>`.

- `<Source>` (nom de source de trace).

- `<Correlation>` (id d’activité défini lors de l’émission de la trace).

- `<Execution>` (id processus et thread).

- `<Computer>`.

- `<ExtendedData>`, y compris `<Action>`, `<MessageID>` et le `<ActivityId>` défini dans l’en-tête de message lors de l’envoi d’un message.

Si vous examinez le suivi "Envoi d'un message sur un canal", vous pouvez consulter le contenu suivant.

```xml
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">
   <System xmlns="http://schemas.microsoft.com/2004/06/windows/eventlog/system">
      <EventID>262163</EventID>
      <Type>3</Type>
      <SubType Name="Information">0</SubType>
      <Level>8</Level>
      <TimeCreated SystemTime="2006-08-04T18:45:30.8491051Z" />
      <Source Name="System.ServiceModel" />
       <Correlation ActivityID="{27c6331d-8998-43aa-a382-03239013a6bd}"/>
       <Execution ProcessName="client" ProcessID="1808" ThreadID="1" />
       <Channel />
       <Computer>TEST1</Computer>
   </System>
   <ApplicationData>
       <TraceData>
          <DataItem>
             <TraceRecord xmlns="http://schemas.microsoft.com/2004/10/E2ETraceEvent/TraceRecord" Severity="Information">
                 <TraceIdentifier>http://msdn.microsoft.com/library/System.ServiceModel.Channels.MessageSent.aspx</TraceIdentifier>
                 <Description>Sent a message over a channel.</Description>
                 <AppDomain>client.exe</AppDomain>
                 <Source>System.ServiceModel.Channels.ClientFramingDuplexSessionChannel/35191196</Source>
                <ExtendedData xmlns="http://schemas.microsoft.com/2006/08/ServiceModel/MessageTransmitTraceRecord">

                  <MessageProperties>
                     <AllowOutputBatching>False</AllowOutputBatching>
                  </MessageProperties>
                  <MessageHeaders>
                     <Action d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">http://Microsoft.ServiceModel.Samples/ICalculator/Multiply</Action>
                     <MessageID xmlns="http://www.w3.org/2005/08/addressing">urn:uuid:7c6670d8-4c9c-496e-b6a0-2ceb6db35338</MessageID>
                     <ActivityId CorrelationId="b02e2189-0816-4387-980c-dd8e306440f5" xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">27c6331d-8998-43aa-a382-03239013a6bd</ActivityId>
                     <ReplyTo xmlns="http://www.w3.org/2005/08/addressing">
                        <Address>http://www.w3.org/2005/08/addressing/anonymous</Address>
                    </ReplyTo>
                    <To d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">net.tcp://localhost/servicemodelsamples/service</To>
                  </MessageHeaders>
                  <RemoteAddress>net.tcp://localhost/servicemodelsamples/service</RemoteAddress>
                </ExtendedData>
            </TraceRecord>
          </DataItem>
       </TraceData>
   </ApplicationData>
</E2ETraceEvent>
```

## <a name="servicemodel-e2e-tracing"></a>Suivi de ServiceModel E2E

Lorsque le `System.ServiceModel` source de trace est définie avec un `switchValue` autre que désactivé, et `ActivityTracing`, WCF crée des activités et transferts pour le traitement de WCF.

Une activité est une unité logique de traitement qui regroupe tous les suivis liés à cette unité de traitement. Par exemple, vous pouvez définir une activité pour chaque demande. Les transferts créent une relation causale entre des activités dans des points de terminaison. Propager l'ID d'activité vous permet de lier des activités sur des points de terminaison. Cela est possible en définissant `propagateActivity` = `true` dans la configuration à chaque point de terminaison. Les activités, les transferts et la propagation vous permettent d'effectuer la corrélation d'erreur. De cette manière, vous pouvez rechercher plus rapidement la cause racine d’une erreur.

Sur le client, une activité WCF est créée pour chaque appel de modèle objet (par exemple, Ouvrir ChannelFactory, ajouter, diviser et ainsi de suite.) Chacun des appels d’opération est traitée dans une activité « Traiter l’Action ».

Dans la capture d’écran suivante, extraite de la [Tracing and Message Logging](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemple le volet gauche affiche la liste des activités créées dans le processus client, triées par heure de création. Vous trouverez ci-dessous une liste chronologique des activités :

- Construction de la fabrication de canal (ClientBase).

- Ouverture de la fabrication de canal.

- Traitement de l'action Add.

- Configurer la Session sécurisée (s’est produite lors de la première demande) et infrastructure de sécurité traité de trois messages de réponse : RST, RSTR, SCT (traiter le message 1, 2, 3).

- Traitement des demandes de soustraction, multiplication et division.

- Fermeture de la fabrication de canal, et ce faisant de la session sécurisée et traitement de la réponse de message de sécurité Cancel.

 Les messages d'infrastructure de sécurité s'affichent à cause de l'élément wsHttpBinding.

> [!NOTE]
> Dans WCF, nous expliquons les messages de réponse qui sont traités initialement dans une activité séparée (traiter le message) avant de les corréler à l’activité traiter l’Action correspondante qui inclut le message de demande, via un transfert. Cette opération a lieu pour les messages d'infrastructure et les demandes asynchrones et tient au fait que nous devons inspecter le message, lire l'en-tête activityId et identifier l'activité Traiter l'action existante avec cet ID pour le corréler. Pour les demandes synchrones, nous attendons la réponse et donc nous savons à quelle activité de traitement d’action se rapporte la réponse.

L’illustration suivante montre des activités clientes WCF répertoriées par heure de création (volet gauche) et leurs activités imbriquées et les traces (volet supérieur droit) :

![Capture d’écran montrant des activités répertoriées par heure de création de client WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)

Lorsque nous sélectionnons une activité dans le volet gauche, le volet supérieur droit affiche des activités et des suivis imbriqués. Par conséquent, il s'agit d'une vue hiérarchique réduite de la liste des activités de gauche basées sur l'activité parente sélectionnée. Comme l'activité « Traiter l'action Add » sélectionnée est la première demande effectuée, cette activité contient l'activité Configurer une session sécurisée (transférer vers, transférer en retour) et les suivis du traitement réel de l'action Ajouter.

En double-cliquant sur l’action de processus ajouter une activité dans le volet gauche, nous pouvons voir une représentation graphique des activités WCF client liés à ajouter. La première activité à gauche est l'activité racine (0000), l'activité par défaut. WCF transfère hors de l’activité ambiante. Si ce n’est pas défini, WCF transfère hors de 0000. Dans ce contexte, la deuxième activité (« Traiter l'action Add ») transfère hors de 0. Elle est suivie de Configurer la session sécurisée.

L’illustration suivante montre une vue du graphique de client WCF activités, en particulier des activité ambiante (ici 0), de traiter l’action et de configurer une Session sécurisée :

![Dans la visionneuse de Trace montrant l’action d’activité ambiante et le processus du graphique.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)

Dans le volet supérieur droit, nous pouvons consulter tous les suivis se rapportant à l'activité Traiter l'action Add. Spécifiquement, nous avons envoyé le message de demande (« Envoi d'un message sur un canal ») et avons reçu la réponse (« Réception d'un message sur un canal ») dans la même activité. Ce cas est illustré dans le graphique suivant. À des fins de clarté, l‘activité Configurer une session sécurisée est réduite dans le graphique.

L’illustration suivante montre une liste des suivis pour l’activité traiter l’Action. Nous envoyer la demande et recevoir la réponse dans la même activité.

![Capture d’écran de visionneuse de Trace affichant une liste de traces pour l’activité traiter l’Action](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)

Ici, nous chargeons suivis clients uniquement par souci de clarté, mais les suivis de service (message de demande reçu et message de réponse envoyé) apparaissent dans la même activité si elles sont également chargés dans l’outil et `propagateActivity` a été défini sur `true.` cela est illustré plus loin.

Sur le service, le modèle d’activité mappe aux concepts WCF comme suit :

1. Nous construisons et ouvrons un ServiceHost (cela peut créer plusieurs activités associées à l'hôte, par exemple, dans le cas de la sécurité).

2. Nous créons une activité Écouter à pour chaque écouteur dans le ServiceHost (avec des transferts en entrée et en sortie de l'activité Ouvrir ServiceHost).

3. Lorsque l’écouteur détecte une demande de communication initiée par le client, elle transfère à une activité « Recevoir des octets », dans lequel tous les octets envoyés depuis le client sont traités. Dans cette activité, nous pouvons voir les erreurs de connexion qui se sont produites pendant l'interaction du service et du client.

4. Pour chaque ensemble d’octets reçu qui correspond à un message, nous traitons ces octets dans une activité « Traiter le Message », où nous créons l’objet Message WCF. Dans cette activité, nous constatons des erreurs dues à un message erroné ou à une enveloppe incorrecte.

5. Une fois que le message est formé, nous transférons à une activité Traiter l'action. Si `propagateActivity` a la valeur `true` sur le client et le service, cette activité a le même identificateur que celui défini dans le client et décrit précédemment. À partir de cette étape nous commençons à bénéficier de la corrélation directe entre les points de terminaison, étant tous les suivis émis dans WCF qui sont liés à la demande à cette même activité, y compris le traitement de message de réponse.

6. Pour l’action out-of-process, nous créons une activité « Exécuter le code utilisateur » pour isoler les suivis émis dans le code utilisateur à partir de ceux émis dans WCF. Dans l’exemple précédent, le suivi de « Service envoie la réponse ajouter » est émis dans l’activité « Exécuter le code utilisateur », pas dans l’activité propagée par le client, le cas échéant.

Dans l'illustration suivante, la première activité à gauche est l'activité racine (0000), l'activité par défaut. Les trois activités suivantes consistent à ouvrir le ServiceHost. L'activité dans la colonne 5 est l'écouteur, et les activités restantes (6 à 8) décrivent le traitement WCF d'un message, du traitement des octets à l'activation du code utilisateur.

L’illustration suivante montre une vue du graphique d’activités de service WCF :

![Capture d’écran de visionneuse de Trace affichant une liste d’activités de service WCF](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)

La capture d'écran suivante affiche les activités pour le client et le service, et met en surbrillance l'activité Traiter l'action Add dans les processus (orange). Les flèches lient les messages de demande et de réponse envoyés et reçus par le client et le service. Les suivis de Traiter l'action sont séparés par processus dans le graphique, mais sont affichés dans le cadre de la même activité dans le volet supérieur droit. Dans ce volet, nous pouvons voir les suivis clients pour les messages envoyés qui précèdent les suivis de service pour les messages reçus et traités.

Les images suivantes indiquent une vue du graphique de ces deux activités de client et le service WCF

![Graphique à partir de la visionneuse de Trace qui montre les deux activités de client et le service WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)

Dans le scénario d'erreur suivant, les suivis d'erreur et d'avertissement au niveau du service et du client sont liés. Une exception est levée d'abord dans le code utilisateur sur le service (activité verte la plus à droite qui inclut un suivi d'avertissement pour l'exception « Le service ne peut pas traiter cette demande dans le code utilisateur »). Lorsque la réponse est envoyée au client, un suivi d'avertissement est encore émis pour désigner le message d'erreur (activité rose à gauche). Le client ferme ensuite son client WCF (activité jaune sur le côté inférieur gauche) qui abandonne la connexion au service. Le service génère une erreur (activité rose la plus longue, à droite).

![À l’aide de la visionneuse de Trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Corrélation d'erreurs dans le service et le client

L’exemple utilisé pour générer ces suivis est une série de demandes synchrones qui utilisent wsHttpBinding. Les scénarios sans sécurité présentent des différences par rapport à ce graphique, ou dans le cas des demandes asynchrones, dans lesquelles l'activité Traiter l'action comprend les opérations de début et de fin qui constituent l'appel asynchrone, et affiche les transferts vers une activité de rappel. Pour plus d’informations sur des scénarios supplémentaires, consultez [scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).

## <a name="troubleshooting-using-the-service-trace-viewer"></a>Résolution des problèmes à l'aide de Service Trace Viewer

Lorsque vous chargez des fichiers de suivi dans l'outil Service Trace Viewer, vous pouvez sélectionner une activité rouge ou jaune dans le volet gauche pour localiser la cause d'un problème dans votre application. En général, l'activité 000 contient des exceptions non prises en charge qui se présentent à l'utilisateur.

L’image suivante montre comment sélectionner une activité rouge ou jaune pour localiser l’origine d’un problème.
![Capture d’écran des activités rouges ou jaunes pour localiser la racine d’un problème.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)

Dans le volet supérieur droit, vous pouvez examiner des suivis de l'activité que vous avez sélectionnée sur la gauche. Vous pouvez examiner ensuite des suivis rouges ou jaunes dans ce volet et observer la manière dont ils sont corrélés. Dans le graphique précédent, nous voyons des suivis d'avertissement à la fois pour le client et le service dans la même activité Traiter l'action.

Si ces suivis n’indiquent pas la cause racine de l’erreur, vous pouvez utiliser le graphique en double-cliquant sur l’activité sélectionnée dans le volet gauche (ici, Traiter l’action). Puis le graphique avec les activités connexes est affiché. Vous pouvez développer des activités connexes (en cliquant sur les signes « + ») pour rechercher le premier suivi émis en rouge ou jaune dans une activité connexe. Continuez à développer les activités qui se sont produites avant le suivi rouge ou jaune présentant un intérêt, les transferts aux flux d’activités ou de messages connexes sur des points de terminaison, jusqu’à ce que vous localisiez l’origine du problème.

![À l’aide de la visionneuse de Trace](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")

Développement des activités pour localiser l’origine d’un problème

Si `ActivityTracing` ServiceModel est désactivé mais le suivi ServiceModel est activé, vous pouvez consulter des suivis ServiceModel émis dans l'activité 0000. Toutefois, la corrélation de ces suivis demande un effort d'interprétation plus grand.

Si l'enregistrement des messages est activé, vous pouvez utiliser l'onglet Message pour voir quel message est concerné par l'erreur. En double-cliquant sur un message en rouge ou en jaune, vous pouvez consulter la vue graphique des activités connexes. Ces activités sont celles qui sont le plus étroitement liées à la demande où une erreur s'est produite.

![Capture d’écran de visionneuse de Trace avec la journalisation des messages est activée.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)

Pour commencer le dépannage, vous pouvez également choisir une trace de message rouge ou jaune et double-cliquer dessus pour effectuer le suivi de la cause racine.

## <a name="see-also"></a>Voir aussi

- [Scénarios de suivi de bout en bout](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Outil Service Trace Viewer (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
