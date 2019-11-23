---
title: Outil de configuration de modèle de service COM+ (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 13368dfa7ca9d7981ac146b87e83f77077eaf537
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320733"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a><span data-ttu-id="216be-102">Outil de configuration de modèle de service COM+ (ComSvcConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="216be-102">COM+ Service Model Configuration Tool (ComSvcConfig.exe)</span></span>
<span data-ttu-id="216be-103">L'outil en ligne de configuration de modèle de service COM+ (ComSvcConfig.exe) permet de configurer des interfaces COM+ à exposer en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="216be-103">The COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) enables you to configure COM+ interfaces to be exposed as Web services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="216be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="216be-104">Syntax</span></span>  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a><span data-ttu-id="216be-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="216be-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="216be-106">Vous devez être administrateur sur l'ordinateur local pour pouvoir utiliser ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="216be-106">You must be an administrator on the local computer to use ComSvcConfig.exe.</span></span>  
  
 <span data-ttu-id="216be-107">Cet outil se trouve à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="216be-107">The tool can be found in the following location</span></span>  
  
 <span data-ttu-id="216be-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="216be-108">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
 <span data-ttu-id="216be-109">Pour plus d’informations sur ComSvcConfig. exe, consultez [Comment : utiliser l’outil de configuration de modèle de service com+](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="216be-109">For more information about ComSvcConfig.exe, see [How to: Use the COM+ Service Model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).</span></span>  
  
 <span data-ttu-id="216be-110">Le tableau suivant décrit les modes qui peuvent être utilisés avec ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="216be-110">The following table describes the modes that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="216be-111">Option</span><span class="sxs-lookup"><span data-stu-id="216be-111">Option</span></span>|<span data-ttu-id="216be-112">Description</span><span class="sxs-lookup"><span data-stu-id="216be-112">Description</span></span>|  
|------------|-----------------|  
|`install`|<span data-ttu-id="216be-113">Installe une configuration d'interface COM+ pour l'intégration du modèle de service.</span><span class="sxs-lookup"><span data-stu-id="216be-113">Installs a configuration for a COM+ interface for Service Model integration.</span></span><br /><br /> <span data-ttu-id="216be-114">Forme abrégée : `/i`.</span><span class="sxs-lookup"><span data-stu-id="216be-114">Short form `/i`.</span></span>|  
|`uninstall`|<span data-ttu-id="216be-115">Désinstalle une configuration d'interface COM+ de l'intégration de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="216be-115">Uninstalls a configuration for a COM+ interface from Service Model integration.</span></span><br /><br /> <span data-ttu-id="216be-116">Forme abrégée : `/u`.</span><span class="sxs-lookup"><span data-stu-id="216be-116">Short form `/u`.</span></span>|  
|`list`|<span data-ttu-id="216be-117">Répertorie les informations relatives aux applications COM+ et aux composants qui possèdent des interfaces configurées pour l'intégration de modèle de service.</span><span class="sxs-lookup"><span data-stu-id="216be-117">Lists information about COM+ applications and components that have interfaces that are configured for Service Model integration.</span></span><br /><br /> <span data-ttu-id="216be-118">Forme abrégée : `/l`.</span><span class="sxs-lookup"><span data-stu-id="216be-118">Short form `/l`.</span></span>|  
  
 <span data-ttu-id="216be-119">Le tableau suivant décrit les indicateurs qui peuvent être utilisés avec ComSvcConfig.exe.</span><span class="sxs-lookup"><span data-stu-id="216be-119">The following table describes the flags that can be used with ComSvcConfig.exe.</span></span>  
  
|<span data-ttu-id="216be-120">Option</span><span class="sxs-lookup"><span data-stu-id="216be-120">Option</span></span>|<span data-ttu-id="216be-121">Description</span><span class="sxs-lookup"><span data-stu-id="216be-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="216be-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span><span class="sxs-lookup"><span data-stu-id="216be-122">`/application:` \<*ApplicationID* &#124; *ApplicationName*\></span></span>|<span data-ttu-id="216be-123">Spécifie l'application COM+ à configurer.</span><span class="sxs-lookup"><span data-stu-id="216be-123">Specifies the COM+ application to configure.</span></span><br /><br /> <span data-ttu-id="216be-124">Forme abrégée : `/a`.</span><span class="sxs-lookup"><span data-stu-id="216be-124">Short form `/a`.</span></span>|  
|<span data-ttu-id="216be-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span><span class="sxs-lookup"><span data-stu-id="216be-125">`/contract:` \<*ClassID*  &#124; *ProgID*  &#124; \*,*InterfaceID* &#124; *InterfaceName* &#124; \*\></span></span>|<span data-ttu-id="216be-126">Spécifie le composant et l'interface COM+ qui seront configurés en tant que contrat pour le service.</span><span class="sxs-lookup"><span data-stu-id="216be-126">Specifies the COM+ component and interface that will be configured as the contract for the service.</span></span><br /><br /> <span data-ttu-id="216be-127">Forme abrégée : `/c`.</span><span class="sxs-lookup"><span data-stu-id="216be-127">Short form `/c`.</span></span><br /><br /> <span data-ttu-id="216be-128">Si vous pouvez utiliser le caractère générique (\*) lorsque vous spécifiez les noms des composants et des interfaces, nous vous recommandons de ne pas l’utiliser, car vous pouvez exposer des interfaces que vous n’avez pas l’intention d’utiliser.</span><span class="sxs-lookup"><span data-stu-id="216be-128">While the wildcard character (\*) can be used when you specify the component and interface names, we recommend that you do not use it, because you might expose interfaces that you did not intend to.</span></span>|  
|<span data-ttu-id="216be-129">`/hosting:` \<*complus*  &#124; *was*\></span><span class="sxs-lookup"><span data-stu-id="216be-129">`/hosting:` \<*complus*  &#124; *was*\></span></span>|<span data-ttu-id="216be-130">Spécifie s'il faut utiliser le mode d'hébergement COM+ ou Web.</span><span class="sxs-lookup"><span data-stu-id="216be-130">Specifies whether to use the COM+ hosting mode or the Web hosting mode.</span></span><br /><br /> <span data-ttu-id="216be-131">Forme abrégée : `/h`.</span><span class="sxs-lookup"><span data-stu-id="216be-131">Short form `/h`.</span></span><br /><br /> <span data-ttu-id="216be-132">L'utilisation du mode d'hébergement COM+ requiert l'activation explicite de l'application COM+.</span><span class="sxs-lookup"><span data-stu-id="216be-132">Using the COM+ hosting mode requires explicit activation of the COM+ application.</span></span> <span data-ttu-id="216be-133">L'utilisation du mode d'hébergement Web permet à l'application COM+ d'être activée automatiquement, de façon appropriée.</span><span class="sxs-lookup"><span data-stu-id="216be-133">Using the Web hosting mode allows the COM+ application to be automatically activated as required.</span></span> <span data-ttu-id="216be-134">Si l'application COM+ est une application de bibliothèque, elle s'exécute au cours du processus de Services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="216be-134">If the COM+ application is a library application, it runs in the Internet Information Services (IIS) process.</span></span> <span data-ttu-id="216be-135">Si l'application COM+ est une application serveur, elle s'exécute au cours du processus Dllhost.exe.</span><span class="sxs-lookup"><span data-stu-id="216be-135">If the COM+ application is a server application, it runs in the Dllhost.exe process.</span></span>|  
|<span data-ttu-id="216be-136">`/webSite:` \<*WebsiteName*\></span><span class="sxs-lookup"><span data-stu-id="216be-136">`/webSite:` \<*WebsiteName*\></span></span>|<span data-ttu-id="216be-137">Spécifie le site web à utiliser pour l’hébergement lorsque le mode d’hébergement Web est utilisé (consultez l’indicateur `/hosting` ).</span><span class="sxs-lookup"><span data-stu-id="216be-137">Specifies the Web site for hosting when Web hosting mode is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="216be-138">Forme abrégée : `/w`.</span><span class="sxs-lookup"><span data-stu-id="216be-138">Short form `/w`.</span></span><br /><br /> <span data-ttu-id="216be-139">Si aucun site Web n'est spécifié, le site Web par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="216be-139">If no Web site is specified, the default Web site is used.</span></span>|  
|<span data-ttu-id="216be-140">`/webDirectory:` \<*WebDirectoryName*\></span><span class="sxs-lookup"><span data-stu-id="216be-140">`/webDirectory:` \<*WebDirectoryName*\></span></span>|<span data-ttu-id="216be-141">Spécifie le répertoire virtuel à utiliser pour l'hébergement lorsque le mode d'hébergement Web est utilisé (consultez l'indicateur `/hosting` ).</span><span class="sxs-lookup"><span data-stu-id="216be-141">Specifies the virtual directory for hosting when Web hosting is used (see the `/hosting` flag).</span></span><br /><br /> <span data-ttu-id="216be-142">Forme abrégée : `/d`.</span><span class="sxs-lookup"><span data-stu-id="216be-142">Short form `/d`.</span></span>|  
|`/mex`|<span data-ttu-id="216be-143">Ajoute un service d'échange de métadonnées (MEX, Metadata Exchange) à la configuration du service par défaut pour prendre en charge les clients qui souhaitent récupérer une définition de contrat à partir du service.</span><span class="sxs-lookup"><span data-stu-id="216be-143">Adds a Metadata Exchange (MEX) service endpoint to the default service configuration to support clients that want to retrieve a contract definition from the service.</span></span><br /><br /> <span data-ttu-id="216be-144">Forme abrégée : `/x`.</span><span class="sxs-lookup"><span data-stu-id="216be-144">Short form `/x`.</span></span>|  
|`/id`|<span data-ttu-id="216be-145">Affiche les informations sur l'application, le composant et l'interface en tant qu'ID.</span><span class="sxs-lookup"><span data-stu-id="216be-145">Displays the application, component, and interface information as IDs.</span></span><br /><br /> <span data-ttu-id="216be-146">Forme abrégée : `/k`.</span><span class="sxs-lookup"><span data-stu-id="216be-146">Short form `/k`.</span></span>|  
|`/nologo`|<span data-ttu-id="216be-147">Empêche ComSvcConfig.exe d'afficher son logo.</span><span class="sxs-lookup"><span data-stu-id="216be-147">Prevents ComSvcConfig.exe from displaying its logo.</span></span><br /><br /> <span data-ttu-id="216be-148">Forme abrégée : `/n`.</span><span class="sxs-lookup"><span data-stu-id="216be-148">Short form `/n`.</span></span>|  
|`/verbose`|<span data-ttu-id="216be-149">Affiche tous les avertissements ou tout le texte informatif en plus des erreurs rencontrées.</span><span class="sxs-lookup"><span data-stu-id="216be-149">Outputs all warnings or informational text in addition to any errors encountered.</span></span><br /><br /> <span data-ttu-id="216be-150">Forme abrégée : `/v`.</span><span class="sxs-lookup"><span data-stu-id="216be-150">Short form `/v`.</span></span>|  
|`/help`|<span data-ttu-id="216be-151">Affiche le message d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="216be-151">Displays the usage message.</span></span><br /><br /> <span data-ttu-id="216be-152">Forme abrégée : `/?`.</span><span class="sxs-lookup"><span data-stu-id="216be-152">Short form `/?`.</span></span>|  
|`/partial`|<span data-ttu-id="216be-153">Génère une configuration de service lorsque l'interface spécifiée inclut une ou plusieurs signatures de méthode qui peuvent être exposées.</span><span class="sxs-lookup"><span data-stu-id="216be-153">Generates a service configuration when the specified interface includes one or more method signatures that can be exposed.</span></span> <span data-ttu-id="216be-154">Au moment de l'initialisation, les méthodes compatibles apparaissent en tant qu'opérations sur le contrat de service, et les méthodes non compatibles sont ignorées et absentes du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="216be-154">At service initialization time, compatible methods appear as operations on the service contract, and non-compatible methods are ignored and absent from the service contract.</span></span><br /><br /> <span data-ttu-id="216be-155">Si cet indicateur est manquant, l'outil ne génère pas de configuration de service lorsque l'interface spécifiée inclut une ou plusieurs méthodes incompatibles.</span><span class="sxs-lookup"><span data-stu-id="216be-155">If this flag is missing, the tool will not generate a service configuration when the specified interface includes one or more incompatible methods.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="216be-156">Exemples</span><span class="sxs-lookup"><span data-stu-id="216be-156">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="216be-157">Description</span><span class="sxs-lookup"><span data-stu-id="216be-157">Description</span></span>  
 <span data-ttu-id="216be-158">L'exemple suivant ajoute l'interface `IFinances` du composant `ItemOrders.IFinancial` (de l'application COM+ OnlineStore) aux interfaces exposées en tant que services Web, à l'aide du mode d'hébergement COM+.</span><span class="sxs-lookup"><span data-stu-id="216be-158">The following example adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that are exposed as Web services, using the COM+ hosting mode.</span></span> <span data-ttu-id="216be-159">Outre les erreurs rencontrées, l'affichage inclut tous les avertissements.</span><span class="sxs-lookup"><span data-stu-id="216be-159">All warnings will be output in addition to any errors encountered.</span></span>  
  
### <a name="code"></a><span data-ttu-id="216be-160">Code</span><span class="sxs-lookup"><span data-stu-id="216be-160">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a><span data-ttu-id="216be-161">Description</span><span class="sxs-lookup"><span data-stu-id="216be-161">Description</span></span>  
 <span data-ttu-id="216be-162">L'exemple suivant illustre l'ajout de l'interface `IStockLevels` du composant `ItemInventory.Warehouse` (de l'application COM+ OnlineWarehouse) aux interfaces exposées en tant que services Web, à l'aide du mode d'hébergement Web.</span><span class="sxs-lookup"><span data-stu-id="216be-162">The following example adds the `IStockLevels` interface of the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that are exposed as Web services, using the Web hosting mode.</span></span> <span data-ttu-id="216be-163">Le service Web est en mode d'hébergement Web dans le répertoire virtuel OnlineWarehouse d'IIS.</span><span class="sxs-lookup"><span data-stu-id="216be-163">The Web service is Web hosted in the OnlineWarehouse virtual directory of IIS.</span></span>  
  
### <a name="code"></a><span data-ttu-id="216be-164">Code</span><span class="sxs-lookup"><span data-stu-id="216be-164">Code</span></span>  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a><span data-ttu-id="216be-165">Description</span><span class="sxs-lookup"><span data-stu-id="216be-165">Description</span></span>  
 <span data-ttu-id="216be-166">L'exemple suivant illustre la suppression de l'interface `IFinances` du composant `ItemOrders.Financial` (de l'application COM+ OnlineStore) du groupe d'interfaces exposées en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="216be-166">The following example removes the `IFinances` interface of the `ItemOrders.Financial` component (from the OnlineStore COM+ application) from the set of interfaces that are exposed as Web services.</span></span>  
  
### <a name="code"></a><span data-ttu-id="216be-167">Code</span><span class="sxs-lookup"><span data-stu-id="216be-167">Code</span></span>  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a><span data-ttu-id="216be-168">Description</span><span class="sxs-lookup"><span data-stu-id="216be-168">Description</span></span>  
 <span data-ttu-id="216be-169">L’exemple suivant répertoire les interfaces actuellement exposées, hébergées par COM+, ainsi que l’adresse correspondante et les détails de liaison, pour l’application COM+ OnlineStore située sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="216be-169">The following example lists currently exposed COM+ hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>  
  
### <a name="code"></a><span data-ttu-id="216be-170">Code</span><span class="sxs-lookup"><span data-stu-id="216be-170">Code</span></span>  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a><span data-ttu-id="216be-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="216be-171">See also</span></span>

- [<span data-ttu-id="216be-172">Guide pratique pour utiliser l’outil de configuration de modèle de service COM+</span><span class="sxs-lookup"><span data-stu-id="216be-172">How to: Use the COM+ Service Model Configuration Tool</span></span>](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)
