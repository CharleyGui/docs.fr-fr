---
title: Publication du service WCF
description: La publication de service WCF vous aide à déployer votre application dans un environnement de production à des fins de test.
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: ccd3fe80e51ef28f7a037d624e9099c42d867d95
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544568"
---
# <a name="wcf-service-publishing"></a>Publication du service WCF

La publication de service Windows Communication Foundation (WCF) vous aide à progresser de l’environnement de développement anticipé fourni par l’hôte de service WCF et le client test WCF pour déployer l’application dans un environnement de production à des fins de test. Avant de vous engager dans un plan de déploiement final, vous pouvez utiliser la publication de service Windows Communication Foundation (WCF) pour vérifier que votre service WCF fonctionne correctement et qu’il est prêt à être publié. Vous pouvez également choisir de déployer vos bibliothèques de service WCF dans différents emplacements cibles à des fins de test.

## <a name="supported-services-and-target-locations"></a>Services pris en charge et emplacements cibles

La publication de service WCF prend en charge la publication de services WCF créés à partir de l’ensemble de modèles de la bibliothèque de services WCF, ainsi que les modèles d’éléments correspondants, qui incluent les éléments suivants :

- Modèle de bibliothèque du service WCF avec modèle d’élément.

- Bibliothèque du service de syndication.

Vous pouvez trouver ces modèles de service en choisissant **fichier**  >  **nouveau projet** > [**Visual Basic** ou **Visual C#**] > **WCF**. Pour les autres modèles WCF à cet emplacement (y compris l’application de service de flux de travail WCF et l’application de service WCF), vous pouvez publier à l’aide [de la publication en un clic pour les applications Web](/previous-versions/aspnet/dd465337(v=vs.110)).

Le service peut être publié aux emplacements cibles suivants.

- IIS local

- Système de fichiers.

- Site FTP

## <a name="using-wcf-service-publishing"></a>Utilisation de la publication de service WCF

Pour déployer une implémentation de service, procédez comme suit :

1. Ouvrez Visual Studio avec des privilèges élevés (cliquez avec le bouton droit sur le fichier exécutable et choisissez **exécuter en tant qu’administrateur** pour l’ouvrir).  Si vous utilisez IIS 7,0 ou une version ultérieure, assurez-vous que vous avez installé le composant « compatibilité avec la métabase IIS et la configuration IIS6 » à l’aide de « activer ou désactiver des fonctionnalités Windows » dans le panneau de configuration.

2. Ouvrez un projet de service, sélectionnez **générer**  >  **publier \<Project Name> ** dans le menu principal, ou cliquez avec le bouton droit sur le projet dans **Explorateur de solutions** puis cliquez sur **publier**.

3. La fenêtre **publier** s’affiche. Cliquez sur **...**. pour spécifier l'emplacement cible où doit être déployé le service. Vous pouvez choisir de déployer l’application sur un site IIS local, un système de fichiers ou un site FTP. Si vous déployez l’application sur un serveur IIS local, vous pouvez sélectionner votre site Web et créer votre application Web sous celui-ci en cliquant sur l’icône **créer une application Web** dans l’angle supérieur droit.

4. Une fois que vous avez cliqué sur **publier** dans la fenêtre principale, Visual Studio déploie l’application à l’emplacement cible spécifié et copie les fichiers d’assembly, de Web.config,. svc et d’assembly dans le répertoire cible. . Le nom de. svc sera « ProjectName. ServiceName. svc ». Une fois que le service a été publié avec succès, vous pouvez trouver un lien hypertexte dans la fenêtre sortie de Visual Studio, qui ressemble à « connexion à `http://localhost/WebApplicationFolderName...` ». Vous pouvez appuyer sur Ctrl et cliquer sur le lien pour ouvrir une page du navigateur dans Visual Studio afin d'afficher la structure des répertoires du service.

     S'il est impossible de visiter le site, l'explorateur de répertoires n'est peut-être pas activé dans IIS. Suivez les conseils de la section « choses que vous pouvez essayer » pour l’activer. Vous pouvez également taper directement `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` pour afficher votre page de service.

Vous pouvez utiliser **publier** pour spécifier si vous souhaitez copier l’assembly, la configuration et le fichier. svc pour tous les services définis dans le projet vers l’emplacement cible, et remplacer les fichiers existants à la destination.

Si vous choisissez de déployer votre application sur le serveur IIS local, vous pouvez rencontrer des erreurs liées à l'installation d'IIS. Vérifiez que IIS est installé correctement. Vous pouvez entrer `http://localhost` dans la barre d’adresse de votre navigateur et vérifier si la page IIS par défaut s’affiche. Dans certains cas, les problèmes peuvent également être dus à une inscription incorrecte de ASP.NET ou WCF dans IIS. Vous pouvez ouvrir le Invite de commandes développeur pour Visual Studio et exécuter la commande `aspnet_regiis.exe -ir` pour résoudre les problèmes d’inscription ASP.net ou exécuter la commande `ServiceModelReg.exe –ia` pour résoudre les problèmes d’inscription WCF.

## <a name="files-generated-for-publishing"></a>Fichiers générés en vue de leur publication
 Pour qu’une bibliothèque de services WCF puisse être hébergée sur le Web, les fichiers suivants sont générés par l’outil : fichiers d’assembly, Web.config fichier et fichier. svc. Tous les fichiers sont copiés à l'emplacement cible. Le service est ensuite publié.

### <a name="assembly-files"></a>Fichiers d'assembly
 Lorsque vous publiez un service WCF à l’aide de cet outil, le service est automatiquement créé en premier et les fichiers d’assembly sont générés dans le projet de service après la génération.

### <a name="svc-file"></a>Fichier .SVC
 L’opération de publication génère un fichier *. svc pour chaque service WCF, que le fichier existe ou non, pour garantir la validité de la version. Il existe deux types différents de fichiers svc : un pour la bibliothèque de services WCF et la bibliothèque du service de syndication, et un autre pour la bibliothèque de service de workflow d’ordinateur séquentiel et d’État. Le \* fichier. svc généré est copié dans le dossier racine de l’emplacement cible.

### <a name="webconfig-file"></a>Fichier Web.config
 Chaque fois qu'un projet de service est publié à un emplacement cible spécifique, un fichier Web.config est créé.

 Le fichier de Web.config généré comprend des sections Web qui sont utiles pour l’hébergement Web, ainsi que le contenu de App.config pour la bibliothèque de services WCF avec les modifications suivantes :

- L'adresse de base est exclue.

- Les paramètres dans l'élément `<diagnostics>` sont exclus pour préserver les paramètres de suivi de la plateforme cible.

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>Publication sur IIS de services WCF avec des liaisons non-HTTP
 Si vous utilisez IIS 7.0 ou version ultérieure, vous pouvez publier des services WCF avec des liaisons non-HTTP vers IIS. Vous devez effectuer plusieurs tâches de préconfiguration. Pour plus d’informations, consultez les rubriques consacrées à l'  [hébergement dans le service d’activation des processus Windows](./feature-details/hosting-in-windows-process-activation-service.md).

## <a name="security"></a>Sécurité
 La publication sur le serveur IIS local requiert des privilèges d'administrateur car IIS doit être exécuté sous un compte Administrateur. Si un utilisateur sans privilège d’administrateur ouvre la publication de service WCF, IIS n’est pas disponible en tant qu’emplacement cible. La publication dans le système de fichiers ou le site FTP fonctionne sans privilège d’administrateur.

## <a name="see-also"></a>Voir aussi

- [Modèles Visual Studio WCF](wcf-vs-templates.md)
- [Hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
