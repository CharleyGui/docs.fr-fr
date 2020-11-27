---
title: Configuration des services Internet (IIS) 7.0 pour Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: 865e19d6626846481347274774d3ea59f2f7ecdd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284210"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a>Configuration des services Internet (IIS) 7.0 pour Windows Communication Foundation

Les services Internet (IIS) 7.0 sont conçus de manière modulaire vous permettant ainsi d'installer uniquement les composants dont vous avez besoin. Cette conception est basée sur la nouvelle technologie de composant basée sur les manifestes introduite dans Windows Vista. Il existe plus de 40 composants de fonctionnalités autonomes d’IIS 7,0 qui peuvent être installés indépendamment. Cela permet aux professionnels de l'informatique de personnaliser plus facilement leur installation en fonction de leurs besoins. Cette rubrique explique comment configurer IIS 7,0 pour une utilisation avec Windows Communication Foundation (WCF) et déterminer quels composants sont requis.

## <a name="minimal-installation-installing-was"></a>Installation minimale : installation du service WAS

 L’installation minimale de l’ensemble du package IIS 7,0 consiste à installer le service d’activation des processus Windows (WAS). WAS est une fonctionnalité autonome qui est la seule fonctionnalité de la version IIS 7,0 qui est disponible pour tous les systèmes d’exploitation Windows Vista (édition familiale basique, édition familiale Premium, entreprise et édition intégrale et entreprise).

 Dans le panneau de configuration, cliquez sur **programmes** , puis sur **activer ou désactiver des fonctionnalités Windows** , qui est répertorié sous **programmes et fonctionnalités**, le composant was est affiché dans la liste comme dans l’illustration suivante.

 ![Boîte de dialogue Activer ou désactiver des fonctionnalités Windows](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")

 Cette fonctionnalité intègre les sous-composants suivants :

- Environnement .NET

- API de configuration

- Modèle de processus

 Si vous sélectionnez le nœud racine de WAS, seul le sous-nœud du **modèle de processus** est activé par défaut. Remarque : dans le cadre de la présente installation, seul le service WAS est installé car la prise en charge d’un serveur web n’est pas assurée.

 Pour que WCF ou toute application ASP.NET fonctionne, activez la case à cocher **environnement .net** . Cela signifie que tous les composants WAS sont requis pour que WCF et ASP.NET fonctionnent bien. Ces composants sont automatiquement activés dès lors que l'un d'entre eux est installé.

## <a name="iis-70-default-installation"></a>IIS 7.0 : installation par défaut

 En activant la fonctionnalité **Internet Information Services** , certains sous-nœuds sont automatiquement vérifiés comme indiqué dans l’illustration suivante.

 ![Paramètres par défaut des fonctionnalités IIS 7.0](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")

 Il s’agit de l’installation par défaut d’IIS 7,0. Avec cette installation, vous pouvez utiliser IIS 7,0 pour traiter du contenu statique (par exemple, des pages HTML et d’autres contenus). Toutefois, vous ne pouvez pas exécuter des applications ASP.NET ou CGI ni héberger des services WCF.

## <a name="iis-70-installation-with-aspnet-support"></a>IIS 7.0 : installation avec prise en charge ASP.NET

 Vous devez installer ASP.NET pour faire fonctionner ASP.NET sur IIS 7,0. Après avoir vérifié **ASP.net**, votre écran doit ressembler à l’illustration suivante.

 ![Paramètres obligatoires Asp.NET](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")

 Il s’agit de l’environnement minimal pour les applications WCF et ASP.NET qui fonctionnent dans IIS 7,0.

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a>IIS 7.0 : installation avec les composants de compatibilité IIS 6.0

 Lors de l’installation d’IIS 7,0 sur un système avec Visual Studio 2005 ou d’autres scripts ou outils d’automatisation (tels que Adsutil.vbs) qui configurent des applications virtuelles qui utilisent l’API de métabase IIS 6,0, veillez à vérifier les **outils de script** IIS 6,0. Cela vérifie automatiquement les autres sous-nœuds de la **compatibilité avec la gestion** d’IIS 6,0. L’illustration suivante montre l’écran à l’issue de cette opération :

 ![Paramètres de compatibilité avec la gestion IIS 6.0](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")

 Avec cette installation, vous avez tout ce dont vous avez besoin pour utiliser IIS 7,0, ASP.NET et les fonctionnalités et exemples WCF disponibles sur le Web.

## <a name="request-limits"></a>Limites de la demande

 Sur Windows Vista avec IIS 7, la valeur par défaut `maxUri` des `maxQueryStringSize` paramètres et a été modifiée. Par défaut, le filtrage de demande dans IIS 7.0 autorise une URL d'une longueur de 4096 caractères et une longueur de chaîne de 2048 caractères. Pour modifier ces valeurs par défaut, ajoutez l'élément XML suivant au fichier App.config.

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a>Voir aussi

- [Architecture d'activation WAS](was-activation-architecture.md)
- [Configuration du service WAS pour une utilisation avec WCF](configuring-the-wpa--service-for-use-with-wcf.md)
- [Procédure : installer et configurer des composants d’activation WCF](how-to-install-and-configure-wcf-activation-components.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))
