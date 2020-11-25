---
title: 'Procédure : utiliser l’outil de configuration de modèle de service COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 2d21ec8ccf84a7c9af235af8e0afd444044cf81b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729385"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a><span data-ttu-id="02516-102">Procédure : utiliser l’outil de configuration de modèle de service COM+</span><span class="sxs-lookup"><span data-stu-id="02516-102">How to: Use the COM+ Service Model Configuration Tool</span></span>

<span data-ttu-id="02516-103">Une fois que vous avez sélectionné un mode d'hébergement approprié, utilisez l'outil en ligne de commande de configuration de modèle de service COM+ (ComSvcConfig.exe) pour configurer les interfaces d'application qui seront exposées en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="02516-103">Once you have selected an appropriate hosting mode, use the COM+ Service Model Configuration command-line tool (ComSvcConfig.exe) to configure the application interfaces that will be exposed as Web services.</span></span>

> [!NOTE]
> <span data-ttu-id="02516-104">Vous devez être administrateur sur l’ordinateur pour exécuter chacune des tâches suivantes.</span><span class="sxs-lookup"><span data-stu-id="02516-104">You must be an administrator on the machine to perform any of the following tasks.</span></span>

 <span data-ttu-id="02516-105">Lorsque vous utilisez ComSvcConfig.exe sur un ordinateur Windows 7 pour configurer un service Web de façon à utiliser la dernière version de modèle de service (v4.5), exécutez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="02516-105">When using ComSvcConfig.exe on a Windows 7 machine to configure a web service to use the latest service model version (currently v4.5), perform the following steps:</span></span>

1. <span data-ttu-id="02516-106">Affectez à la clé de Registre  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` une valeur DWORD 0x00000001.</span><span class="sxs-lookup"><span data-stu-id="02516-106">Set the registry key  `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` to a DWORD value of 0x00000001</span></span>

2. <span data-ttu-id="02516-107">Exécutez comsvcconfig.exe.</span><span class="sxs-lookup"><span data-stu-id="02516-107">Run comsvcconfig.exe</span></span>

3. <span data-ttu-id="02516-108">Rétablissez la valeur par défaut de la clé de Registre ajoutée à l'étape 1, ou supprimez -la si elle n'existait pas.</span><span class="sxs-lookup"><span data-stu-id="02516-108">Revert the registry key added in step 1 back to its original value, or delete it if did not exist.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="02516-109">Il est important de rétablir cette clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="02516-109">Reverting this registry key is important.</span></span> <span data-ttu-id="02516-110">Il s'agit d'une clé de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="02516-110">This is a compatibility key.</span></span> <span data-ttu-id="02516-111">Le fait de ne pas rétablir cette modification peut provoquer des problèmes avec d'autres applications .NET en cours de exécution sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="02516-111">Not reverting this change may cause issues with other .NET applications running on the machine).</span></span>

> [!WARNING]
> <span data-ttu-id="02516-112">Quand vous utilisez ComSvcConfig.exe/install sur un ordinateur Windows 8, une boîte de dialogue s’affiche indiquant « une application sur votre PC a besoin de la fonctionnalité Windows suivante : .NET Framework 3,5 (comprend .NET 2,0 et .NET 3,0 » si .NET Framework 3,5 n’est pas installée.</span><span class="sxs-lookup"><span data-stu-id="02516-112">When using ComSvcConfig.exe  /install on a Windows 8 machine, a dialog is displayed stating "An app on your PC needs the following Windows feature: .NET Framework 3.5 (includes .NET 2.0 and .NET 3.0" if .NET Framework 3.5 is not installed.</span></span> <span data-ttu-id="02516-113">Cette boîte de dialogue peut être ignorée.</span><span class="sxs-lookup"><span data-stu-id="02516-113">This dialog may be ignored.</span></span> <span data-ttu-id="02516-114">Vous pouvez aussi affecter à la clé de Registre OnlyUseLatestCLR la valeur DWORD 0x00000001.</span><span class="sxs-lookup"><span data-stu-id="02516-114">Alternatively you can sed the OnlyUseLatestCLR registry key to a DWORD value of 0x00000001</span></span>

## <a name="add-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="02516-115">Ajouter une interface à l’aide du mode d’hébergement COM+</span><span class="sxs-lookup"><span data-stu-id="02516-115">Add an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="02516-116">Exécutez ComSvcConfig avec les options `/install` et `/hosting:complus`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-116">Run ComSvcConfig using the `/install` and `/hosting:complus` options, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose
    ```

     <span data-ttu-id="02516-117">La commande ajoute l'interface `IFinances` du composant `ItemOrders.IFinancial` (depuis l'application COM+ OnlineStore) à l'ensemble des interfaces qui seront exposées en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="02516-117">The command adds the `IFinances` interface of the `ItemOrders.IFinancial` component (from the OnlineStore COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="02516-118">Le service utilise le mode d'hébergement COM+, et requiert par conséquent l'activation d'application explicite.</span><span class="sxs-lookup"><span data-stu-id="02516-118">The service uses the COM+ hosting mode and therefore requires explicit application activation.</span></span>

     <span data-ttu-id="02516-119">Si le caractère générique astérisque ( \* ) peut être utilisé pour le composant et l’interface, évitez de l’utiliser, car vous souhaiterez peut-être exposer uniquement les fonctionnalités sélectionnées en tant que service Web.</span><span class="sxs-lookup"><span data-stu-id="02516-119">While the wildcard asterisk (\*) character can be used for the component and the interface, avoid using it because you might want to expose only selected functionality as a Web service.</span></span> <span data-ttu-id="02516-120">En cas d'exécution avec une version ultérieure de ce composant, l'utilisation du caractère générique peut exposer involontairement des interfaces qui étaient peut-être absentes lorsque la syntaxe de configuration a été déterminée.</span><span class="sxs-lookup"><span data-stu-id="02516-120">If run with a future version of this component, using the wildcard may unintentionally expose interfaces that may not have been present when the configuration syntax was determined.</span></span>

     <span data-ttu-id="02516-121">L'option /verbose fait en sorte que l'outil affiche des avertissements en plus des éventuelles erreurs.</span><span class="sxs-lookup"><span data-stu-id="02516-121">The /verbose option instructs the tool to display warnings in addition to any errors.</span></span>

     <span data-ttu-id="02516-122">Le contrat pour le service exposé contiendra toutes les méthodes de l'interface `IFinances`.</span><span class="sxs-lookup"><span data-stu-id="02516-122">The contract for the exposed service will contain all of the methods from the `IFinances` interface.</span></span>

## <a name="add-specific-methods-from-an-interface-using-the-com-hosting-mode"></a><span data-ttu-id="02516-123">Ajouter des méthodes spécifiques à partir d’une interface à l’aide du mode d’hébergement COM+</span><span class="sxs-lookup"><span data-stu-id="02516-123">Add specific methods from an interface using the COM+ hosting mode</span></span>

- <span data-ttu-id="02516-124">Exécutez ComSvcConfig avec les options `/install` et `/hosting:complus` et avec la désignation explicite des méthodes requises, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-124">Run ComSvcConfig using the `/install` and `/hosting:complus` options with explicit naming of the required methods, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose
    ```

     <span data-ttu-id="02516-125">La commande ajoute uniquement les méthodes `Credit` et `Debit` de l'interface `IFinances` comme opérations au contrat de service exposé.</span><span class="sxs-lookup"><span data-stu-id="02516-125">The command adds only the `Credit` and `Debit` methods from the `IFinances` interface as operations to the exposed service contract.</span></span> <span data-ttu-id="02516-126">Toutes les autres méthodes sur l'interface seront omises du contrat et ne pourront pas être appelées à partir de clients de service Web.</span><span class="sxs-lookup"><span data-stu-id="02516-126">All other methods on the interface will be omitted from the contract and will not be callable from Web service clients.</span></span>

## <a name="add-an-interface-using-the-web-hosting-mode"></a><span data-ttu-id="02516-127">Ajouter une interface à l’aide du mode d’hébergement Web</span><span class="sxs-lookup"><span data-stu-id="02516-127">Add an interface using the Web hosting mode</span></span>

- <span data-ttu-id="02516-128">Exécutez ComSvcConfig avec les options `/install` et `/hosting:was`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-128">Run ComSvcConfig using the `/install` option and the `/hosting:was` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose
    ```

     <span data-ttu-id="02516-129">La commande ajoute l'interface `IStockLevels` sur le composant `ItemInventory.Warehouse` (depuis l'application COM+ OnlineWarehouse) à l'ensemble des interfaces qui seront exposées en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="02516-129">The command adds the `IStockLevels` interface on the `ItemInventory.Warehouse` component (from the OnlineWarehouse COM+ application) to the set of interfaces that will be exposed as Web services.</span></span> <span data-ttu-id="02516-130">Le service étant hébergé sur le Web dans le répertoire virtuel OnlineWarehouse des services Internet (IIS) plutôt que dans COM+, l'application est activée automatiquement selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="02516-130">The service is Web hosted in the OnlineWarehouse virtual directory of IIS rather than in COM+, and thus the application is automatically activated as required.</span></span>

     <span data-ttu-id="02516-131">Pour utiliser la configuration hébergée sur le Web dans un processus, l'application COM+ doit être configurée pour s'exécuter en tant qu'application bibliothèque plutôt qu'application serveur à l'aide de la console d'administration Services de composants.</span><span class="sxs-lookup"><span data-stu-id="02516-131">To use the Web-hosted in-process configuration, the COM+ application must be configured to run as a Library application rather than a Server application using the Component Services administration console.</span></span> <span data-ttu-id="02516-132">Les applications configurées en tant qu'applications serveur utilisent le mode hébergé sur le Web standard et effectuent un saut de processus pour traiter chaque demande.</span><span class="sxs-lookup"><span data-stu-id="02516-132">Applications configured as Server applications use the standard Web-hosted mode and incur a process hop to process each request.</span></span>

     <span data-ttu-id="02516-133">L'option `/mex` ajoute un point de terminaison de service Échange de métadonnées (MEX) supplémentaire qui utilise le même transport que le point de terminaison de service de l'application pour prendre en charge les clients qui souhaitent récupérer une définition de contrat à partir du service.</span><span class="sxs-lookup"><span data-stu-id="02516-133">The `/mex` option adds an additional Metadata Exchange (MEX) service endpoint that uses the same transport as the application's service endpoint to support clients that want to retrieve a contract definition from the service.</span></span>

## <a name="remove-a-web-service-for-a-specified-interface"></a><span data-ttu-id="02516-134">Supprimer un service Web pour une interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="02516-134">Remove a Web service for a specified interface</span></span>

- <span data-ttu-id="02516-135">Exécutez ComSvcConfig avec l'option `/uninstall`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-135">Run ComSvcConfig using the `/uninstall` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus
    ```

     <span data-ttu-id="02516-136">La commande supprime l'interface `IFinances` sur le composant `ItemOrders.Financial` (de l'application COM+ OnlineStore).</span><span class="sxs-lookup"><span data-stu-id="02516-136">The command removes the `IFinances` interface on the `ItemOrders.Financial` component (from the OnlineStore COM+ application).</span></span>

## <a name="list-currently-exposed-interfaces"></a><span data-ttu-id="02516-137">Répertorier les interfaces actuellement exposées</span><span class="sxs-lookup"><span data-stu-id="02516-137">List currently exposed interfaces</span></span>

- <span data-ttu-id="02516-138">Exécutez ComSvcConfig avec l'option `/list`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-138">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list
    ```

     <span data-ttu-id="02516-139">La commande répertoire les interfaces actuellement exposées, avec l’adresse correspondante et les détails de liaison, avec comme étendue l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="02516-139">The command lists the currently exposed interfaces, along with the corresponding address and binding details, scoped to the local machine.</span></span>

## <a name="list-specific-currently-exposed-interfaces"></a><span data-ttu-id="02516-140">Répertorier des interfaces actuellement exposées</span><span class="sxs-lookup"><span data-stu-id="02516-140">List specific currently exposed interfaces</span></span>

- <span data-ttu-id="02516-141">Exécutez ComSvcConfig avec l'option `/list`, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-141">Run ComSvcConfig using the `/list` option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus
    ```

     <span data-ttu-id="02516-142">La commande répertoire les interfaces hébergées par COM+ exposées actuellement, avec l’adresse correspondante et les détails de liaison, pour l’application COM+ OnlineStore sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="02516-142">The command lists currently exposed COM+-hosted interfaces, along with the corresponding address and binding details, for the OnlineStore COM+ application on the local machine.</span></span>

## <a name="display-help-for-options"></a><span data-ttu-id="02516-143">Afficher l’aide pour les options</span><span class="sxs-lookup"><span data-stu-id="02516-143">Display help for options</span></span>

- <span data-ttu-id="02516-144">Exécutez ComSvcConfig à l'aide de l'option /?,</span><span class="sxs-lookup"><span data-stu-id="02516-144">Run ComSvcConfig using the /?</span></span> <span data-ttu-id="02516-145">tel qu'illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="02516-145">option, as shown in the following example.</span></span>

    ```console
    ComSvcConfig.exe /?
    ```

## <a name="see-also"></a><span data-ttu-id="02516-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02516-146">See also</span></span>

- [<span data-ttu-id="02516-147">Vue d’ensemble de l’intégration aux applications COM+</span><span class="sxs-lookup"><span data-stu-id="02516-147">Integrating with COM+ Applications Overview</span></span>](integrating-with-com-plus-applications-overview.md)
