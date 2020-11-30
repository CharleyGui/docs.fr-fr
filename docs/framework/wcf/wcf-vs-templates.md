---
title: Modèles Visual Studio WCF
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: a3aa7e3ee57759ef54ddaa898fe036c4e3caa33e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2020
ms.locfileid: "96279699"
---
# <a name="wcf-visual-studio-templates"></a>Modèles Visual Studio WCF

Les modèles Visual Studio Windows Communication Foundation (WCF) sont des modèles de projet et d’élément prédéfinis que vous pouvez utiliser dans Visual Studio pour générer rapidement des services WCF et des applications environnantes.  
  
## <a name="using-the-wcf-templates"></a>Utilisation des modèles WCF  

 Les modèles Visual Studio WCF fournissent une structure de classe de base pour le développement de services. Spécifiquement, ces modèles fournissent les définitions de base pour les contrats de service, les contrats de données, les implémentations de services et les configurations. Vous pouvez utiliser ces modèles pour créer un service simple avec une interaction minimale du code, ainsi qu'un bloc de création pour des services plus avancés.  
  
### <a name="wcf-service-library-project-template"></a>Modèle de projet Bibliothèque du service WCF  

 Le modèle de projet Bibliothèque du service WCF est disponible dans la boîte de dialogue Nouveau projet sous **Visual C# \WCF** et **Visual Basic\WCF**.  
  
 Lorsque vous créez un projet à l’aide du modèle de **service WCF** , le nouveau projet comprend automatiquement les trois fichiers suivants :  
  
- Fichier de contrat de service (IService1.cs ou IService1.vb). Le fichier de contrat de service est une interface à laquelle sont appliqués les attributs de service WCF. Ce fichier contient la définition d'un service simple destinée à vous aider à définir vos services et inclut des opérations basées des paramètres, ainsi qu'un exemple de contrat de données simple. Il s’agit du fichier par défaut affiché dans l’éditeur de code après la création d’un projet de service WCF.  
  
- Fichier d'implémentation de service (Service1.cs ou Service1.vb). Le fichier d'implémentation de service implémente le contrat défini dans le fichier de contrat de service.  
  
- Fichier de configuration de l'application (App.config). Le fichier de configuration fournit les éléments de base d’un modèle de service WCF avec une liaison HTTP sécurisée. Il inclut également un point de terminaison applicable au service et active l'échange de métadonnées.  
  
> [!NOTE]
> Visual Studio est configuré pour reconnaître le fichier App.config comme fichier de configuration pour le projet lorsqu’il est exécuté à l’aide de l' [hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md), qui est la configuration par défaut. Si la bibliothèque de services se trouve dans un fichier exécutable, vous devez déplacer le code de configuration vers le fichier de configuration du fichier exécutable : en effet, les fichiers de configuration des DLL ne sont pas valides.  
  
### <a name="wcf-service-application-template"></a>Modèle d'application de service WCF  

 Le modèle application de service WCF est disponible dans la boîte de dialogue Nouveau projet sous **Visual C# \WCF** et **Visual Basic\WCF**.  
  
 Lorsque vous créez un projet à l’aide du modèle de **service d’application Web WCF** , le projet comprend les quatre fichiers suivants :  
  
- Fichier d'hôte de service (service1.svc).  
  
- Fichier de contrat de service (IService1.cs ou IService1.vb).  
  
- Fichier d'implémentation de service (Service1.svc.cs ou Service1.svc.vb).  
  
- Fichier de configuration Web (Web.config).  
  
 Le modèle crée automatiquement un site Web (à déployer dans un répertoire virtuel) et y héberge un service.  
  
### <a name="wcf-web-site-template"></a>Modèle de site Web WCF  

 Le modèle de site Web WCF est disponible dans la boîte de dialogue Nouveau projet sous **Visual C# \Web Site\WCF service** et **Visual Basic\Web Site\WCF service**. Cela crée les mêmes fichiers que ceux du modèle d’application de service WCF, mais les classe comme s’il s’agissait d’un site web ASP.NET. Les dossiers App_Code et App_Data sont créés.  
  
### <a name="wcf-service-item-template"></a>Modèle d'élément de service WCF  

 Le modèle d’élément de service WCF est un modèle personnalisé qui fournit un moyen rapide d’ajouter des services WCF à vos projets Visual Studio existants.  
  
 Pour utiliser ce modèle, accédez au volet **Explorateur de solutions** , cliquez avec le bouton droit sur le nom de votre projet, pointez sur **Ajouter**, puis cliquez sur **nouvel élément** pour ouvrir la boîte de dialogue **Ajouter un nouvel élément** .  
  
 L'interface de service et les fichiers d'implémentation sont placés dans le dossier du projet racine.  
  
 Le modèle tente de fusionner la section de configuration du nouveau service avec le fichier de configuration existant, si leurs types sont compatibles.  
  
 Un fichier d'hôte de service (service1.svc) est également créé si le projet existant est un projet Web.  
  
### <a name="wcf-wf-service-project-and-item-template"></a>Modèles d'élément et de projet de service WF WCF.  

 Ces modèles créent des services WCF qui hébergent un service de flux de travail, qui est un flux de travail accessible comme un service Web. Différents modèles existent pour les XAML et les modèles de programmation impératifs. À l'aide des modèles, vous pouvez créer des workflows séquentiels ou des workflows de l'ordinateur d'état. Pour plus d’informations sur ces types de flux de travail, consultez [Comment : créer un flux de travail](../windows-workflow-foundation/how-to-create-a-workflow.md). Pour plus d’informations sur la création de projets de workflow, consultez [création de projets de workflow hérités](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).  
  
 Le concepteur Visual Studio est plus réactif lorsque les workflows de type XOML sont utilisés à la place de code basé sur du code. Le workflow XOML est le type de workflow par défaut à créer.  
  
### <a name="wcf-syndication-service-library-template"></a>Modèle de la bibliothèque du service de syndication WCF  

 Ce modèle vous permet d’exposer votre flux au format RSS ou ATOM en tant que service WCF. Pour plus d’informations, consultez [syndication WCF](./feature-details/wcf-syndication.md).  
  
#### <a name="changing-the-address-of-the-feed"></a>Modification de l'adresse du flux  

 Le modèle de syndication utilise Internet Explorer au cours de l'exécution. Quand vous cliquez avec le bouton droit sur votre projet dans l' **Explorateur de solutions** dans Visual Studio, sélectionnez **Propriétés**, puis sélectionnez l’onglet **Déboguer** . vous pouvez voir l’adresse par défaut du modèle. Internet Explorer tente d'ouvrir le flux à cette adresse.  
  
 Si vous modifiez l’adresse de votre flux, vous devez également modifier l’adresse dans l’onglet **Déboguer** . Si vous ne le faites pas, Internet Explorer tente d’ouvrir le flux à l’adresse par défaut et échoue.  
  
### <a name="ajax-enabled-wcf-service-item-template"></a>Modèle d'élément de service WCF AJAX  

 Ce modèle expose un contrôle AJAX en tant que service WCF. Pour plus d’informations sur les contrôles AJAX, consultez la [documentation relative au contrôle AJAX](/aspnet/ajax/).  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a>Modèle d'élément de service WCF compatible Silverlight  

 Ce modèle crée un service Web qui fournit des données à un client Silverlight ou frontal. Le modèle peut être ajouté à un site Web ou à un projet d’application Web pour créer un service WCF, qui comprend le code de service et la configuration qui prennent en charge la communication avec un client Silverlight. Vous pouvez ensuite utiliser **Ajouter une référence de service** pour ajouter un proxy client du service au client et échanger des données entre le client Silverlight et le service WCF compatible Silverlight.  
  
 Pour accéder à ce modèle, cliquez avec le bouton droit sur un site Web ou un projet d’application Web dans **Explorateur de solutions**, cliquez sur **Ajouter un nouvel élément**, puis cliquez sur **service WCF compatible Silverlight**.  
  
> [!NOTE]
> Le service WCF compatible Silverlight expose un point de terminaison `basicHttpBinding` sans activer de paramètre de sécurité. Par conséquent, les informations concernant le service peuvent être obtenues par tous les clients qui s'y connectent. Les messages échangés entre le service et le client ne sont pas signés ni chiffrés. Pour sécuriser correctement le point de terminaison, vous devez utiliser l'authentification ASP.NET, HTTPS ou d'autres mécanismes.  
  
## <a name="see-also"></a>Voir aussi

- [Hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
- [Client test WCF (WcfTestClient.exe)](wcf-test-client-wcftestclient-exe.md)
