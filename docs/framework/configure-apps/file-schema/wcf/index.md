---
title: Schéma de configuration WCF
ms.date: 03/30/2017
ms.assetid: c282aeb5-91f0-4522-8e2f-704c1ef3651f
ms.openlocfilehash: ab64b41e6e79c934ac0145dd7eec0a943f5dc473
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165128"
---
# <a name="wcf-configuration-schema"></a><span data-ttu-id="556ce-102">Schéma de configuration WCF</span><span class="sxs-lookup"><span data-stu-id="556ce-102">WCF Configuration Schema</span></span>

<span data-ttu-id="556ce-103">Les éléments de configuration Windows Communication Foundation (WCF) vous permettent de configurer des applications clientes et de service WCF.</span><span class="sxs-lookup"><span data-stu-id="556ce-103">Windows Communication Foundation (WCF) configuration elements enable you to configure WCF service and client applications.</span></span> <span data-ttu-id="556ce-104">Vous pouvez utiliser l’[outil Éditeur de configuration (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) pour créer et modifier des fichiers de configuration pour les clients et les services.</span><span class="sxs-lookup"><span data-stu-id="556ce-104">You can use the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../wcf/configuration-editor-tool-svcconfigeditor-exe.md) to create and modify configuration files for clients and services.</span></span> <span data-ttu-id="556ce-105">Les fichiers de configuration étant au format XML, il est nécessaire de maîtriser ce format pour pouvoir modifier ces fichiers à l'aide d'un éditeur de texte,</span><span class="sxs-lookup"><span data-stu-id="556ce-105">Since the configuration files are formatted as XML, you must be familiar with XML if you want to manually edit them using a text editor.</span></span> <span data-ttu-id="556ce-106">sans quoi vous risquez de rencontrer des problèmes tels qu'une balise ou un attribut d'élément XML manquant.</span><span class="sxs-lookup"><span data-stu-id="556ce-106">Otherwise, you may run into issues such as an unfound XML element tag or attribute.</span></span> <span data-ttu-id="556ce-107">Ce problème a lieu car les étiquettes et les attributs d’éléments XML respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="556ce-107">This is because XML element tags and attributes are case-sensitive.</span></span>  
  
 <span data-ttu-id="556ce-108">Le système de configuration WCF est basé sur l' <xref:System.Configuration> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="556ce-108">The WCF configuration system is based on the <xref:System.Configuration> namespace.</span></span> <span data-ttu-id="556ce-109">Par conséquent, vous pouvez utiliser toutes les fonctionnalité standard fournies par l’espace de noms <xref:System.Configuration>, tel que le verrouillage, le chiffrement et la fusion de la configuration, afin de renforcer la sécurité de votre application et sa configuration.</span><span class="sxs-lookup"><span data-stu-id="556ce-109">Therefore, you can use all the standard features provided by the <xref:System.Configuration> namespace, such as configuration locking, encryption and merging to increase the security of your application and its configuration.</span></span> <span data-ttu-id="556ce-110">Pour plus d'informations sur ces concepts, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="556ce-110">For more information on these concepts, see the following topics.</span></span>  
  
 <span data-ttu-id="556ce-111">[Chiffrement des informations de configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="556ce-111">[Encrypting Configuration Information](/previous-versions/aspnet/53tyfkaw(v=vs.100))</span></span>  
  
 <span data-ttu-id="556ce-112">[Verrouillage des paramètres de configuration](/previous-versions/aspnet/55th21y4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="556ce-112">[Locking Configuration Settings](/previous-versions/aspnet/55th21y4(v=vs.100))</span></span>  
  
 <span data-ttu-id="556ce-113">Cette section décrit toutes les valeurs possibles de chaque élément de configuration et leur interaction avec d'autres éléments de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="556ce-113">This section describes all possible values of each configuration item, and how it interacts with other WCF configuration elements.</span></span> <span data-ttu-id="556ce-114">La carte suivante illustre le schéma de configuration WCF :</span><span class="sxs-lookup"><span data-stu-id="556ce-114">The following map illustrates the WCF configuration schema:</span></span>  
  
 ![Diagramme qui montre le schéma de configuration WCF.](./media/index/windows-communication-foundation-configuration-schema.gif)  
  
> [!CAUTION]
> <span data-ttu-id="556ce-116">Vous devez protéger les sections de configuration WCF dans vos fichiers de configuration d’application (app.config) avec des listes de Access Control appropriées pour éviter toute menace potentielle pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="556ce-116">You should protect WCF configuration sections in your application configuration files (app.config) with appropriate Access Control Lists (ACL) to prevent any potential security threats.</span></span>  <span data-ttu-id="556ce-117">Par exemple, vous devez vous assurer que seules les personnes appropriées peuvent accéder ou modifier les paramètres de sécurité relatifs aux liaisons d’application ou la section relative au modèle de service figurant dans le fichier de configuration d’un service.</span><span class="sxs-lookup"><span data-stu-id="556ce-117">For example, you should make sure that only the appropriate people can access or modify the security settings on application bindings, or the service model section of the configuration file for a service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="556ce-118">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="556ce-118">In This Section</span></span>  

 [\<system.serviceModel>](system-servicemodel.md)  
 <span data-ttu-id="556ce-119">Décrit l'élément `ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="556ce-119">Describes the `ServiceModel` element.</span></span>  
  
 [\<system.serviceModel.activation>](system-servicemodel-activation.md)  
 <span data-ttu-id="556ce-120">Configure l'outil SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="556ce-120">Configures the SMSvcHost.exe tool.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
 <span data-ttu-id="556ce-121">Élément de niveau supérieur permettant de définir les options lors de l'utilisation de sérialiseurs tels que le <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="556ce-121">The top-level element for setting options when using serializers such as the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="556ce-122">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="556ce-122">Related Sections</span></span>  

 [<span data-ttu-id="556ce-123">Configuring Windows Communication Foundation Applications</span><span class="sxs-lookup"><span data-stu-id="556ce-123">Configuring Windows Communication Foundation Applications</span></span>](../../../wcf/configuring-services.md)  
 <span data-ttu-id="556ce-124">Décrit comment configurer les clients et les services WCF.</span><span class="sxs-lookup"><span data-stu-id="556ce-124">Describes how to configure WCF services and clients.</span></span>
