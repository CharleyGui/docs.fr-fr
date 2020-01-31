---
title: Exemples de scénarios d’entreprise et de cas d’utilisation pour les applications sans serveur
description: Découvrez sans serveur une approche pratique en accédant à des exemples qui vont du traitement d’image aux serveurs back-end mobiles et aux pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787895"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scénarios métier et cas d’usage serverless

Il existe de nombreux scénarios et scénarios d’utilisation pour les applications sans serveur. Ce chapitre contient des exemples qui illustrent les différents scénarios. Les scénarios incluent des liens vers la documentation connexe et les référentiels de code source publics. Les exemples de ce chapitre vous permettent de commencer à créer et à mettre en œuvre des solutions sans serveur.

## <a name="analyze-and-archive-images"></a>Analyser et archiver des images

Cet exemple illustre les événements sans serveur (Event Grid), les flux de travail (application logique) et le code (Azure Functions). Il montre également comment intégrer à une autre ressource, dans ce cas Cognitive Services pour l’analyse d’images.

Une application console vous permet de passer un lien vers une URL sur le Web. L’application publie l’URL en tant que message de grille d’événements. En parallèle, une application de fonction sans serveur et une application logique s’abonnent au message. L’application de fonction sans serveur sérialise l’image dans le stockage d’objets BLOB. Il stocke également des informations dans le stockage table Azure. Les métadonnées stockent l’URL de l’image d’origine et le nom de l’image de l’objet BLOB. L’application logique interagit avec l’API Custom Vision pour analyser l’image et créer une légende générée par l’ordinateur. La légende est stockée dans la table de métadonnées.

![Analyser et archiver les images architecture](./media/image-processing-example.png)

Une application à page unique (SPA) distincte appelle une fonction sans serveur pour obtenir une liste d’images et de métadonnées. Pour chaque image, elle appelle une autre fonction qui remet les données de l’image à partir de l’archive. Le résultat final est une galerie avec des légendes automatiques.

![Galerie d’images automatisées](./media/automated-image-gallery.png)

Le référentiel complet et les instructions permettant de générer l’application logique sont disponibles ici : [Collage](https://github.com/JeremyLikness/Event-Grid-Glue)dans la grille d’événements.

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Client mobile multiplateforme utilisant Xamarin. Forms et des fonctions

Découvrez comment implémenter une fonction Azure simple sans serveur dans le portail Web Azure ou dans Visual Studio. Générez un client avec Xamarin. Forms qui s’exécute sur Android, iOS et Windows. L’application est ensuite affinée pour utiliser JavaScript Object Notation (JSON) comme un support de communication entre le serveur et les clients mobiles avec un back end sans serveur.

Pour plus d’informations, consultez [implémentation d’une fonction Azure simple avec un client Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Générer une mosaïque de photos avec reconnaissance d’image sans serveur

L’exemple utilise Azure Functions et Microsoft Cognitive Services Service Vision personnalisée pour générer une mosaïque de photos à partir d’une image d’entrée. Le modèle est formé pour reconnaître les images. Lorsqu’une image est téléchargée, elle reconnaît l’image et recherche avec Bing. L’image d’origine est recomposée à l’aide des résultats de la recherche.

![Photo et mosaïque de Orlando](./media/orlando-eye-both.png)

Par exemple, vous pouvez former votre modèle avec des points de vue Orlando, tels que l’œil-Orlando. Custom Vision reconnaîtra une image de l’œil à Orlando, et la fonction créera une photo Mosaic composée de résultats de recherche d’images Bing pour « Orlando Eye ».

Pour plus d’informations, consultez [Azure Functions générateur de mosaïques de photos](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrer une application existante vers le Cloud

Comme nous l’avons vu dans les chapitres précédents, il est courant d’adopter une architecture multiniveau pour héberger votre application en local. Bien que la migration des ressources « en l’or » à l’aide de machines virtuelles soit le chemin le moins risqué du Cloud, de nombreuses entreprises choisissent d’utiliser l’opportunité de refactoriser leurs applications. Heureusement, la refactorisation ne doit pas nécessairement être un effort « tout ou rien ». En fait, il est possible de migrer votre application, puis de remplacer les composants par fragments par des équivalents Cloud natifs.

L’application utilise la fonctionnalité proxys de Azure Functions pour permettre la refactorisation d’un point de terminaison à partir d’un code local hérité vers un point de terminaison sans serveur.

![Architecture de la migration](./media/migration-architecture.png)

Le proxy fournit un point de terminaison d’API unique qui est mis à jour pour rediriger les demandes individuelles au fur et à mesure qu’elles sont déplacées dans des fonctions sans serveur.

Vous pouvez afficher une vidéo qui vous guide tout au long de la migration : [élévation et décalage avec Azure Functions sans serveur](https://channel9.msdn.com/Events/Connect/2017/E102). Accédez à l’exemple de code : [apportez votre propre application](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Analyser un fichier CSV et l’insérer dans une base de données

L’extraction, la transformation et le chargement (ETL) est une fonction métier courante qui intègre différents systèmes. Les approches traditionnelles impliquent souvent la configuration de serveurs FTP dédiés, puis le déploiement de tâches planifiées pour analyser les fichiers et les traduire pour une utilisation professionnelle. L’architecture sans serveur facilite le travail, car un déclencheur peut se déclencher lorsque le fichier est téléchargé. Azure Functions s’attaque à des tâches telles que ETL par le biais de sa composition idéale de petits morceaux de code qui se concentrent sur un problème spécifique.

![Capture d’écran montrant le processus d’analyse des volumes partagés de cluster.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Pour obtenir le code source et un atelier pratique, consultez [laboratoire d’importation CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Raccourcissez les liens et suivez les mesures

Les outils de raccourci de liaison ont aidé à l’origine à coder les URL dans de courtes publications Twitter pour s’adapter à la limite de 140 caractères. Ils ont augmenté pour englober plusieurs utilisations, le plus souvent pour assurer le suivi des analyses. Le scénario Link raccourcisseur est une application entièrement sans serveur qui gère les liens et signale les métriques.

Azure Functions est utilisé pour traiter une application à page unique (SPA) qui vous permet de coller l’URL longue et de générer des URL courtes. Les URL sont marquées pour effectuer le suivi des éléments tels que des campagnes (rubriques) et des supports (tels que les réseaux sociaux dans lesquels les liens sont publiés). Le code bref est stocké dans le stockage table Azure comme clé, avec l’URL longue comme valeur. Lorsque vous cliquez sur le lien Short, une autre fonction recherche l’URL longue, envoie une redirection et place des informations sur l’événement dans une file d’attente. Une autre fonction Azure traite la file d’attente et place les informations dans Azure Cosmos DB.

![Lier l’architecture raccourcisseur](./media/link-shortener-architecture.png)

Vous pouvez ensuite créer un tableau de bord Power BI pour collecter des informations sur les données collectées. Sur la back end, Application Insights fournit des mesures importantes. La télémétrie comprend le temps nécessaire à la redirection de l’utilisateur moyen et le temps nécessaire pour accéder au stockage table Azure.

![Exemple de Power BI](./media/power-bi-example.png)

Le référentiel raccourcisseur des liens complets avec des instructions est disponible ici : [URL sans serveur raccourcisseur](https://github.com/jeremylikness/serverless-url-shortener). Vous pouvez en savoir plus sur une version simplifiée ici : [stockage Azure pour les applications .net sans serveur en quelques minutes](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Vérifier la connectivité de l’appareil à l’aide d’une commande ping

L’exemple se compose d’une IoT Hub Azure et d’une fonction Azure. Un nouveau message sur le IoT Hub déclenche la fonction Azure. Le code sans serveur renvoie le même contenu de message à l’appareil qui l’a envoyé. Le projet dispose de tout le code et de la configuration de déploiement requis pour la solution.

Pour plus d’informations, consultez [Azure IOT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping).

## <a name="recommended-resources"></a>Ressources recommandées

- [Générateur de mosaïque de photos Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Test ping Azure IoT Hub](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Stockage Azure pour les applications .NET sans serveur en quelques minutes](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Apporter votre propre application](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Laboratoire d’importation CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Collage dans la grille d’événements](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Implémentation d’une fonction Azure simple avec un client Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Tirez et passez avec Azure Functions sans serveur](https://channel9.msdn.com/Events/Connect/2017/E102)
- [URL sans serveur raccourcisseur](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Précédent](orchestration-patterns.md)
>[Suivant](serverless-conclusion.md)
