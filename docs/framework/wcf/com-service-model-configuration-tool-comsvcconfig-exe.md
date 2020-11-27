---
title: Outil de configuration de modèle de service COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: ee0fb5f08446b03485f97de0037e898415016fea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295273"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="c51b5-102">Outil de configuration de modèle de service COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="c51b5-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>

<span data-ttu-id="c51b5-103">L'outil en ligne de configuration de modèle de service COM+ (ComSvcConfig.exe) permet de configurer des interfaces COM+ à exposer en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="c51b5-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c51b5-104">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c51b5-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c51b5-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c51b5-106">Vous devez être administrateur sur l'ordinateur local pour pouvoir utiliser ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c51b5-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="c51b5-107">Cet outil se trouve à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="c51b5-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="c51b5-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c51b5-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="c51b5-109">Pour plus d’informations sur ComSvcConfig.exe, consultez [Comment : utiliser l’outil de configuration de modèle de service com+](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c51b5-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="c51b5-110">Le tableau suivant décrit les modes qui peuvent être utilisés avec ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c51b5-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="c51b5-111">Option</span><span class="sxs-lookup"><span data-stu-id="c51b5-111">Option</span></span>|<span data-ttu-id="c51b5-112">Description</span><span class="sxs-lookup"><span data-stu-id="c51b5-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="c51b5-113">Installe une configuration d'interface COM+ pour l'intégration du modèle de service.</span><span class="sxs-lookup"><span data-stu-id="c51b5-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="c51b5-114">Forme abrégée : `/i`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="c51b5-115">Désinstalle une configuration d'interface COM+ de l'intégration de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="c51b5-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="c51b5-116">Forme abrégée : `/u`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="c51b5-117">Répertorie les informations relatives aux applications COM+ et aux composants qui possèdent des interfaces configurées pour l'intégration de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="c51b5-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="c51b5-118">Forme abrégée : `/l`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="c51b5-119">Le tableau suivant décrit les indicateurs qui peuvent être utilisés avec ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="c51b5-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="c51b5-120">Option</span><span class="sxs-lookup"><span data-stu-id="c51b5-120">Option</span></span>|<span data-ttu-id="c51b5-121">Description</span><span class="sxs-lookup"><span data-stu-id="c51b5-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c51b5-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="c51b5-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="c51b5-123">Spécifie l'application COM+ à configurer.</span><span class="sxs-lookup"><span data-stu-id="c51b5-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="c51b5-124">Forme abrégée : `/a`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="c51b5-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="c51b5-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="c51b5-126">Spécifie le composant et l'interface COM+ qui seront configurés en tant que contrat pour le service.</span><span class="sxs-lookup"><span data-stu-id="c51b5-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="c51b5-127">Forme abrégée : `/c`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="c51b5-128">Si le caractère générique ( \* ) peut être utilisé lorsque vous spécifiez les noms de composant et d’interface, nous vous recommandons de ne pas l’utiliser, car vous pouvez exposer des interfaces que vous n’avez pas l’intention d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="c51b5-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="c51b5-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="c51b5-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="c51b5-130">Spécifie s'il faut utiliser le mode d'hébergement COM+ ou Web.</span><span class="sxs-lookup"><span data-stu-id="c51b5-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="c51b5-131">Forme abrégée : `/h`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="c51b5-132">L'utilisation du mode d'hébergement COM+ requiert l'activation explicite de l'application COM+.</span><span class="sxs-lookup"><span data-stu-id="c51b5-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="c51b5-133">L'utilisation du mode d'hébergement Web permet à l'application COM+ d'être activée automatiquement, de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="c51b5-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="c51b5-134">Si l'application COM+ est une application de bibliothèque, elle s'exécute au cours du processus de Services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="c51b5-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="c51b5-135">Si l'application COM+ est une application serveur, elle s'exécute au cours du processus Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="c51b5-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="c51b5-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="c51b5-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="c51b5-137">Spécifie le site web à utiliser pour l’hébergement lorsque le mode d’hébergement Web est utilisé (consultez l’indicateur `/hosting` ).</span><span class="sxs-lookup"><span data-stu-id="c51b5-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="c51b5-138">Forme abrégée : `/w`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="c51b5-139">Si aucun site Web n'est spécifié, le site Web par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="c51b5-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="c51b5-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="c51b5-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="c51b5-141">Spécifie le répertoire virtuel à utiliser pour l'hébergement lorsque le mode d'hébergement Web est utilisé (consultez l'indicateur `/hosting` ).</span><span class="sxs-lookup"><span data-stu-id="c51b5-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="c51b5-142">Forme abrégée : `/d`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="c51b5-143">Ajoute un service d'échange de métadonnées (MEX, Metadata Exchange) à la configuration du service par défaut pour prendre en charge les clients qui souhaitent récupérer une définition de contrat à partir du service.</span><span class="sxs-lookup"><span data-stu-id="c51b5-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="c51b5-144">Forme abrégée : `/x`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="c51b5-145">Affiche les informations sur l'application, le composant et l'interface en tant qu'ID.</span><span class="sxs-lookup"><span data-stu-id="c51b5-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="c51b5-146">Forme abrégée : `/k`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="c51b5-147">Empêche ComSvcConfig.exe d'afficher son logo.</span><span class="sxs-lookup"><span data-stu-id="c51b5-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="c51b5-148">Forme abrégée : `/n`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="c51b5-149">Affiche tous les avertissements ou tout le texte informatif en plus des erreurs rencontrées.</span><span class="sxs-lookup"><span data-stu-id="c51b5-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="c51b5-150">Forme abrégée : `/v`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="c51b5-151">Affiche le message d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="c51b5-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="c51b5-152">Forme abrégée : `/?`.</span><span class="sxs-lookup"><span data-stu-id="c51b5-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="c51b5-153">Génère une configuration de service lorsque l'interface spécifiée inclut une ou plusieurs signatures de méthode qui peuvent être exposées.</span><span class="sxs-lookup"><span data-stu-id="c51b5-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="c51b5-154">Au moment de l'initialisation, les méthodes compatibles apparaissent en tant qu'opérations sur le contrat de service, et les méthodes non compatibles sont ignorées et absentes du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="c51b5-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="c51b5-155">Si cet indicateur est manquant, l'outil ne génère pas de configuration de service lorsque l'interface spécifiée inclut une ou plusieurs méthodes incompatibles.</span><span class="sxs-lookup"><span data-stu-id="c51b5-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="c51b5-156">Exemples</span><span class="sxs-lookup"><span data-stu-id="c51b5-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="c51b5-157">Description</span><span class="sxs-lookup"><span data-stu-id="c51b5-157">Description</span></span>  

 <span data-ttu-id="c51b5-158">L'exemple suivant ajoute l'interface `IFinances` du composant `ItemOrders.IFinancial` (de l'application COM+ OnlineStore) aux interfaces exposées en tant que services Web, à l'aide du mode d'hébergement COM+.</span><span class="sxs-lookup"><span data-stu-id="c51b5-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="c51b5-159">Outre les erreurs rencontrées, l'affichage inclut tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="c51b5-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c51b5-160">Code</span><span class="sxs-lookup"><span data-stu-id="c51b5-160">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="c51b5-161">Description</span><span class="sxs-lookup"><span data-stu-id="c51b5-161">Description</span></span>  

 <span data-ttu-id="c51b5-162">L'exemple suivant illustre l'ajout de l'interface `IStockLevels` du composant `ItemInventory.Warehouse` (de l'application COM+ OnlineWarehouse) aux interfaces exposées en tant que services Web, à l'aide du mode d'hébergement Web.</span><span class="sxs-lookup"><span data-stu-id="c51b5-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="c51b5-163">Le service Web est en mode d'hébergement Web dans le répertoire virtuel OnlineWarehouse d'IIS.</span><span class="sxs-lookup"><span data-stu-id="c51b5-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c51b5-164">Code</span><span class="sxs-lookup"><span data-stu-id="c51b5-164">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="c51b5-165">Description</span><span class="sxs-lookup"><span data-stu-id="c51b5-165">Description</span></span>  

 <span data-ttu-id="c51b5-166">L'exemple suivant illustre la suppression de l'interface `IFinances` du composant `ItemOrders.Financial` (de l'application COM+ OnlineStore) du groupe d'interfaces exposées en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="c51b5-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c51b5-167">Code</span><span class="sxs-lookup"><span data-stu-id="c51b5-167">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="c51b5-168">Description</span><span class="sxs-lookup"><span data-stu-id="c51b5-168">Description</span></span>  

 <span data-ttu-id="c51b5-169">L’exemple suivant répertoire les interfaces actuellement exposées, hébergées par COM+, ainsi que l’adresse correspondante et les détails de liaison, pour l’application COM+ OnlineStore située sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c51b5-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c51b5-170">Code</span><span class="sxs-lookup"><span data-stu-id="c51b5-170">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="c51b5-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c51b5-171">See also</span></span>

- [<span data-ttu-id="c51b5-172">Procédure : utiliser l’outil de configuration de modèle de service COM+</span><span class="sxs-lookup"><span data-stu-id="c51b5-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
