---
title: Modèles Visual Studio WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: 13183ad5f05350c34eebd025eca3faa7d97644f8
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608021"
---
# <a name="wcf-visual-studio-templates"></a>Modèles Visual Studio WCF
Les modèles Visual Studio de la Windows Communication Foundation (WCF) sont des modèles de projets et d’éléments prédéfinis que vous pouvez utiliser dans Visual Studio pour construire rapidement les services WCF et les applications environnantes.  
  
## <a name="using-the-wcf-templates"></a>Utilisation des modèles WCF  
 Les modèles WCF Visual Studio fournissent une structure de classe de base pour le développement de services. Spécifiquement, ces modèles fournissent les définitions de base pour les contrats de service, les contrats de données, les implémentations de services et les configurations. Vous pouvez utiliser ces modèles pour créer un service simple avec une interaction minimale du code, ainsi qu'un bloc de création pour des services plus avancés.  
  
### <a name="wcf-service-library-project-template"></a>Modèle de projet Bibliothèque du service WCF  
 Le modèle de projet de la bibliothèque de service WCF est disponible dans la nouvelle boîte de dialogue de projet sous **Visual C-WCF** et **Visual Basic-WCF**.  
  
 Lorsque vous créez un nouveau projet à l’aide du modèle **de service WCF,** le nouveau projet inclut automatiquement les trois fichiers suivants :  
  
- Fichier de contrat de service (IService1.cs ou IService1.vb). Le fichier contrat de service est une interface qui a des attributs de service WCF appliqués. Ce fichier contient la définition d'un service simple destinée à vous aider à définir vos services et inclut des opérations basées des paramètres, ainsi qu'un exemple de contrat de données simple. Il s’agit du fichier par défaut affiché dans l’éditeur de code après la création d’un projet de service WCF.  
  
- Fichier d'implémentation de service (Service1.cs ou Service1.vb). Le fichier d'implémentation de service implémente le contrat défini dans le fichier de contrat de service.  
  
- Fichier de configuration de l'application (App.config). Le fichier de configuration fournit les éléments de base d’un modèle de service WCF avec une liaison HTTP sécurisée. Il inclut également un point de terminaison applicable au service et active l'échange de métadonnées.  
  
> [!NOTE]
> Visual Studio est configuré pour reconnaître le fichier App.config comme le fichier de configuration pour le projet lorsqu’il est exécuté à l’aide de [l’hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md), qui est la configuration par défaut. Si la bibliothèque de services se trouve dans un fichier exécutable, vous devez déplacer le code de configuration vers le fichier de configuration du fichier exécutable : en effet, les fichiers de configuration des DLL ne sont pas valides.  
  
### <a name="wcf-service-application-template"></a>Modèle d'application de service WCF  
 Le modèle d’application de service WCF est disponible dans la boîte de dialogue du nouveau projet sous **Visual C-WCF** et **Visual Basic-WCF**.  
  
 Lorsque vous créez un nouveau projet à l’aide du modèle **WCF Web Application Service,** le projet comprend les quatre fichiers suivants :  
  
- Fichier d'hôte de service (service1.svc).  
  
- Fichier de contrat de service (IService1.cs ou IService1.vb).  
  
- Fichier d'implémentation de service (Service1.svc.cs ou Service1.svc.vb).  
  
- Fichier de configuration Web (Web.config).  
  
 Le modèle crée automatiquement un site Web (à déployer dans un répertoire virtuel) et y héberge un service.  
  
### <a name="wcf-web-site-template"></a>Modèle de site Web WCF  
 Le modèle de site Web de WCF est disponible dans la boîte de dialogue du nouveau projet sous **le service Visual C-Web Site-WCF** et **Visual Basic-Web Site-WCF Service**. Cela crée les mêmes fichiers que ceux du modèle d’application de service WCF, mais les classe comme s’il s’agissait d’un site web ASP.NET. Les dossiers App_Code et App_Data sont créés.  
  
### <a name="wcf-service-item-template"></a>Modèle d'élément de service WCF  
 Le modèle D’article de service WCF est un modèle personnalisé qui fournit un moyen rapide d’ajouter des services WCF à vos projets visual Studio existants.  
  
 Pour utiliser ce modèle, rendez-vous sur le volet **Solution Explorer,** cliquez à droite sur le nom de votre projet, pointez **vers ajouter,** puis cliquez sur **Nouvel Élément** pour lancer la boîte de dialogue Add **New Item.**  
  
 L'interface de service et les fichiers d'implémentation sont placés dans le dossier du projet racine.  
  
 Le modèle tente de fusionner la section de configuration du nouveau service avec le fichier de configuration existant, si leurs types sont compatibles.  
  
 Un fichier d'hôte de service (service1.svc) est également créé si le projet existant est un projet Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Modèles d'élément et de projet de service WF WCF.  
 Ces modèles créent des services WCF qui hébergent un service workflow, qui est un flux de travail qui peut être consulté comme un service Web. Différents modèles existent pour les XAML et les modèles de programmation impératifs. À l'aide des modèles, vous pouvez créer des workflows séquentiels ou des workflows de l'ordinateur d'état. Pour plus d’informations sur ces types de flux de travail, voir [Comment : Créer un flux de travail](../windows-workflow-foundation/how-to-create-a-workflow.md). Pour plus d’informations sur la création de projets de flux de travail, voir [Créer des projets de flux de travail hérités](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Visual Studio designer est plus réactif lorsque les flux de travail de type XOML sont utilisés au lieu de ceux basés sur le code. Le workflow XOML est le type de workflow par défaut à créer.  
  
### <a name="wcf-syndication-service-library-template"></a>Modèle de la bibliothèque du service de syndication WCF  
 Ce modèle vous permet d’exposer votre flux dans le format RSS ou ATOM en tant que service WCF. Pour plus d’informations, voir [WCF Syndication](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Modification de l'adresse du flux  
 Le modèle de syndication utilise Internet Explorer au cours de l'exécution. Lorsque vous cliquez à droite sur votre projet dans **Solutions Explorer** dans Visual Studio, sélectionnez **Properties,** puis sélectionnez l’onglet **Debug** et vous pouvez voir l’adresse par défaut du modèle. Internet Explorer tente d'ouvrir le flux à cette adresse.  
  
 Si vous modifiez l’adresse de votre flux, vous devez également modifier l’adresse de l’onglet **Debug.** Si vous ne le faites pas, Internet Explorer tente d’ouvrir le flux à l’adresse par défaut et échoue.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Modèle d'élément de service WCF AJAX  
 Ce modèle expose un contrôle AJAX en tant que service WCF. Pour plus d’informations sur les contrôles AJAX, consultez la [documentation de contrôle AJAX](/aspnet/ajax/).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Modèle d'élément de service WCF compatible Silverlight  
 Ce modèle crée un service Web qui fournit des données à un client Silverlight ou frontal. Le modèle peut être ajouté à un site Web ou à un projet d’application Web pour créer un service WCF, qui comprend le code de service et la configuration qui prennent en charge la communication avec un client Silverlight. Vous pouvez ensuite utiliser **Add Service Reference** pour ajouter un proxy client du service au client et échanger des données entre le client Silverlight et le service WCF compatible Silverlight.  
  
 Pour accéder à ce modèle, cliquez à droite sur un site Web ou un projet d’application Web dans **Solution Explorer**, cliquez sur Ajouter un **nouvel article**, et cliquez sur **Silverlight-enabled WCF Service**.  
  
> [!NOTE]
> Le service WCF compatible Silverlight expose un point de terminaison `basicHttpBinding` sans activer de paramètre de sécurité. Par conséquent, les informations concernant le service peuvent être obtenues par tous les clients qui s'y connectent. Les messages échangés entre le service et le client ne sont pas signés ni chiffrés. Pour sécuriser correctement le point de terminaison, vous devez utiliser l'authentification ASP.NET, HTTPS ou d'autres mécanismes.  
  
## <a name="see-also"></a>Voir aussi

- [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
