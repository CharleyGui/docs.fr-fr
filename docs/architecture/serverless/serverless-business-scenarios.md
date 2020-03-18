---
title: Échantillonnez des scénarios d’affaires et utilisez des cas pour des applications sans serveur
description: Apprenez sans serveur avec une approche pratique en accédant à des échantillons qui vont du traitement d’image aux back ends mobiles et aux pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787895"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scénarios métier et cas d’usage serverless

Il existe de nombreux cas d’utilisation et des scénarios pour les applications sans serveur. Ce chapitre comprend des échantillons qui illustrent les différents scénarios. Les scénarios comprennent des liens vers la documentation connexe et les dépôts de code source publique. Les échantillons de ce chapitre vous permettent de démarrer sur votre propre bâtiment et la mise en œuvre de solutions sans serveur.

## <a name="analyze-and-archive-images"></a>Analyser et archiver des images

Cet exemple montre des événements sans serveur (Event Grid), des flux de travail (Application Logique) et du code (Fonctions Azure). Il montre également comment s’intégrer à une autre ressource, dans ce cas, les services cognitifs pour l’analyse d’image.

Une application console vous permet de passer un lien vers une URL sur le web. L’application publie l’URL sous forme de message de grille d’événements. En parallèle, une application de fonction sans serveur et une application logique s’abonnent au message. L’application de fonction sans serveur sérialisse l’image en stockage blob. Il stocke également des informations dans Azure Table Storage. Les métadonnées stocke l’URL d’image originale et le nom de l’image blob. L’application logique interagit avec l’API Custom Vision pour analyser l’image et créer une légende générée par la machine. La légende est stockée dans la table des métadonnées.

![Analyser et archiver l’architecture des images](./media/image-processing-example.png)

Une application distincte d’une seule page (SPA) appelle une fonction sans serveur pour obtenir une liste d’images et de métadonnées. Pour chaque image, il appelle une autre fonction qui fournit les données d’image de l’archive. Le résultat final est une galerie avec des légendes automatiques.

![Galerie d’images automatisée](./media/automated-image-gallery.png)

Le référentiel complet et les instructions pour construire l’application logique sont disponibles ici: [Colle de grille d’événements](https://github.com/JeremyLikness/Event-Grid-Glue).

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a>Client mobile multiplateforme utilisant Xamarin.Forms et fonctions

Découvrez comment implémenter une simple fonction Azure sans serveur dans le portail Web Azure ou dans Visual Studio. Construisez un client avec Xamarin.Forms qui fonctionne sur Android, iOS et Windows. L’application est ensuite affinée pour utiliser JavaScript Object Notation (JSON) comme moyen de communication entre le serveur et les clients mobiles avec un back-end sans serveur.

Pour plus d’informations, voir [Implémenter une fonction Azure simple avec un client Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a>Générer une mosaïque photo avec reconnaissance d’image sans serveur

L’échantillon utilise Azure Functions et Microsoft Cognitive Services Custom Vision Service pour générer une mosaïque photo à partir d’une image d’entrée. Le modèle est formé pour reconnaître les images. Lorsqu’une image est téléchargée, elle reconnaît l’image et les recherches avec Bing. L’image originale est recomposée à l’aide des résultats de recherche.

![Photo et mosaïque d’oeil d’Orlando](./media/orlando-eye-both.png)

Par exemple, vous pouvez former votre modèle avec des monuments d’Orlando, tels que l’Orlando Eye. Custom Vision reconnaîtra une image de l’Orlando Eye, et la fonction créera une mosaïque photo composée de résultats de recherche d’images Bing pour "Orlando Eye."

Pour plus d’informations, voir [Azure Functions générateur de mosaïque photo](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).

## <a name="migrate-an-existing-application-to-the-cloud"></a>Migrer une application existante vers le cloud

Comme nous l’avons vu dans les chapitres précédents, il est courant d’adopter une architecture N-Tier pour héberger votre application sur place. Bien que la migration des ressources " telle qu’elle soit " à l’aide de machines virtuelles soit le chemin le moins risqué vers le cloud, de nombreuses entreprises choisissent d’en profiter pour refactoriser leurs applications. Heureusement, la refactoration n’a pas besoin d’être un effort " tout ou rien ". En fait, il est possible de migrer votre application puis de remplacer les composants par des homologues natifs du cloud.

L’application utilise la fonction de mandat d’Azure Functions pour permettre de refactoriser un point de terminaison allant du code existant sur place à un point de terminaison sans serveur.

![Architecture de la migration](./media/migration-architecture.png)

Le proxy fournit un point de terminaison API unique qui est mis à jour pour réacheminer les demandes individuelles au fur et à mesure qu’elles sont transférées dans des fonctions sans serveur.

Vous pouvez voir une vidéo qui marche à travers toute la migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102). Accédez au code de l’échantillon : [apportez votre propre application](https://github.com/JeremyLikness/bring-own-app-connect-17).

## <a name="parse-a-csv-file-and-insert-into-a-database"></a>Parse un fichier CSV et insérez dans une base de données

Extrait, Transform, and Load (ETL) est une fonction commerciale commune qui intègre différents systèmes. Les approches traditionnelles impliquent souvent la mise en place de serveurs FTP dédiés, puis le déploiement d’emplois réguliers pour analyser les fichiers et les traduire pour une utilisation commerciale. L’architecture sans serveur facilite le travail car un déclencheur peut se déclencher lorsque le fichier est téléchargé. Azure Functions aborde des tâches comme ETL à travers sa composition idéale de petits morceaux de code qui se concentrent sur un problème spécifique.

![Capture d’écran qui montre le processus d’analyse de csv.](./media/serverless-business-scenarios/csv-parse-database-import.png)

Pour le code source et un laboratoire pratique, voir [CSV laboratoire d’importation](https://github.com/JeremyLikness/azure-fn-file-process-hol).

## <a name="shorten-links-and-track-metrics"></a>Raccourcir les liens et suivre les mesures

Les outils de raccourcissement des liens ont aidé à coder les URL dans de courts messages Twitter pour tenir compte de la limite de 140 caractères. Ils ont grandi pour englober plusieurs utilisations, le plus souvent pour suivre les clics pour l’analyse. Le scénario de raccourcisseur de lien est une application entièrement sans serveur qui gère les liens et les mesures de rapports.

Azure Functions est utilisé pour servir une application à une page unique (SPA) qui vous permet de coller l’URL longue et de générer des URL courtes. Les URL sont étiquetées pour suivre des choses comme les campagnes (sujets) et les médiums (tels que les réseaux sociaux que les liens sont affichés à). Le code court est stocké dans Azure Table Storage comme clé, avec l’URL longue que la valeur. Lorsque vous cliquez sur le lien court, une autre fonction recherche l’URL longue, envoie une redirection, et place des informations sur l’événement sur une file d’attente. Une autre fonction Azure traite la file d’attente et place les informations dans Azure Cosmos DB.

![Lien architecture shortener](./media/link-shortener-architecture.png)

Vous pouvez ensuite créer un tableau de bord Power BI pour recueillir des informations sur les données collectées. À l’arrière, Application Insights fournit des mesures importantes. La télémétrie comprend le temps qu’il faut à l’utilisateur moyen pour rediriger et combien de temps il faut pour accéder au stockage de table Azure.

![Exemple Power BI](./media/power-bi-example.png)

Le référentiel de raccourcisseur de lien complet avec des instructions est disponible ici : [raccourcisseur d’URL sans serveur](https://github.com/jeremylikness/serverless-url-shortener). Vous pouvez lire sur une version simplifiée ici: [Azure Storage pour les applications .NET sans serveur en quelques minutes](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).

## <a name="verify-device-connectivity-using-a-ping"></a>Vérifier la connectivité de l’appareil à l’aide d’un ping

L’échantillon se compose d’un hub Azure IoT et d’une fonction Azure. Un nouveau message sur le hub IoT déclenche la fonction Azure. Le code sans serveur envoie le même contenu de message à l’appareil qui l’a envoyé. Le projet dispose de tout le code et la configuration de déploiement nécessaires à la solution.

Pour plus d’informations, voir [Azure IoT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping).

## <a name="recommended-resources"></a>Ressources recommandées

- [Générateur de mosaïques photo Azure Functions](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [Test ping d’Azure IoT Hub](https://github.com/Azure-Samples/iot-hub-node-ping)
- [Stockage Azure pour les applications .NET sans serveur en quelques minutes](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [Apportez votre propre application](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [Laboratoire d’importation CSV](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [Colle de grille d’événement](https://github.com/JeremyLikness/Event-Grid-Glue)
- [Mise en œuvre d’une fonction Azure simple avec un client Xamarin.Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Soulevez et changez avec des fonctions Azure sans serveur](https://channel9.msdn.com/Events/Connect/2017/E102)
- [Raccourcisseur d’URL sans serveur](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
>[Suivant précédent](orchestration-patterns.md)
>[Next](serverless-conclusion.md)
