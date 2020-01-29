---
title: Commande dotnet nuget push
description: La commande dotnet nuget push exécute un envoi (push) d’un package sur le serveur et le publie.
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: a483c559dee8b4a82cc2c792f5c2c5e4a8ff3f87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733111"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="0edf0-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0edf0-103">dotnet nuget push</span></span>

<span data-ttu-id="0edf0-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="0edf0-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="0edf0-105">Name</span><span class="sxs-lookup"><span data-stu-id="0edf0-105">Name</span></span>

<span data-ttu-id="0edf0-106">`dotnet nuget push` - Exécute un push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="0edf0-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0edf0-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="0edf0-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="0edf0-108">Description</span><span class="sxs-lookup"><span data-stu-id="0edf0-108">Description</span></span>

<span data-ttu-id="0edf0-109">La commande `dotnet nuget push` exécute un push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="0edf0-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="0edf0-110">La commande push utilise les informations serveur et d’identification trouvées dans le fichier ou la chaîne de fichiers de configuration NuGet du système.</span><span class="sxs-lookup"><span data-stu-id="0edf0-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="0edf0-111">Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ).</span><span class="sxs-lookup"><span data-stu-id="0edf0-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="0edf0-112">La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="0edf0-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="0edf0-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0edf0-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="0edf0-114">Spécifie le chemin de fichier au package devant faire l’objet d’un envoi (push).</span><span class="sxs-lookup"><span data-stu-id="0edf0-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="0edf0-115">Options</span><span class="sxs-lookup"><span data-stu-id="0edf0-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="0edf0-116">Désactive la mise en mémoire tampon pendant le transfert push vers un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="0edf0-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="0edf0-117">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="0edf0-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0edf0-118">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0edf0-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="0edf0-119">Autorise la commande pour bloquer et exige une action manuelle pour des opérations comme l'authentification.</span><span class="sxs-lookup"><span data-stu-id="0edf0-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="0edf0-120">Option disponible à partir du SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="0edf0-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="0edf0-121">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="0edf0-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="0edf0-122">N’envoie pas les symboles (même s’ils sont présents).</span><span class="sxs-lookup"><span data-stu-id="0edf0-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="0edf0-123">N’ajoute pas « api/v2/package » à l’URL source.</span><span class="sxs-lookup"><span data-stu-id="0edf0-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="0edf0-124">Option disponible à partir du kit SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="0edf0-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="0edf0-125">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="0edf0-125">Specifies the server URL.</span></span> <span data-ttu-id="0edf0-126">Cette option est obligatoire, sauf si la valeur de configuration de `DefaultPushSource` est définie dans le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="0edf0-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`--skip-duplicate`**

  <span data-ttu-id="0edf0-127">Lors du push de plusieurs packages sur un serveur HTTP (S), traite toute réponse de conflit 409 comme un avertissement afin que l’envoi puisse continuer.</span><span class="sxs-lookup"><span data-stu-id="0edf0-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="0edf0-128">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0edf0-128">Available since .NET Core 3.1 SDK.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="0edf0-129">Clé d’API pour le serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="0edf0-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="0edf0-130">Spécifie l’URL du serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="0edf0-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="0edf0-131">Spécifie le délai d’attente, en secondes, pour effectuer un push vers un serveur.</span><span class="sxs-lookup"><span data-stu-id="0edf0-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="0edf0-132">La valeur par défaut est 300 secondes (5 minutes).</span><span class="sxs-lookup"><span data-stu-id="0edf0-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="0edf0-133">Si vous spécifiez 0 (zéro seconde), la valeur par défaut s’applique.</span><span class="sxs-lookup"><span data-stu-id="0edf0-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="0edf0-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="0edf0-134">Examples</span></span>

* <span data-ttu-id="0edf0-135">Envoie (push) *foo.nupkg* à la source de push par défaut, en spécifiant une clé API :</span><span class="sxs-lookup"><span data-stu-id="0edf0-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="0edf0-136">Envoyez (push) *foo.nupkg* à la source de push personnalisée `https://customsource`, en spécifiant une clé API :</span><span class="sxs-lookup"><span data-stu-id="0edf0-136">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="0edf0-137">Effectuer une transmission de type push de *foo.nupkg* vers la source de push par défaut :</span><span class="sxs-lookup"><span data-stu-id="0edf0-137">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="0edf0-138">Effectuer une transmission de type push de *foo.symbols.nupkg* vers la source de symboles par défaut :</span><span class="sxs-lookup"><span data-stu-id="0edf0-138">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="0edf0-139">Envoie (push) *foo.nupkg* à la source de push par défaut, en spécifiant un délai d’attente de 360 secondes :</span><span class="sxs-lookup"><span data-stu-id="0edf0-139">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="0edf0-140">Effectuer une transmission de type push de tous les fichiers *.nupkg* du répertoire actif vers la source de push par défaut :</span><span class="sxs-lookup"><span data-stu-id="0edf0-140">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="0edf0-141">Si cette commande ne fonctionne pas, cela peut être dû à un bogue qui existait dans les versions antérieures du SDK (Kit SDK .NET Core 2.1 et versions antérieures).</span><span class="sxs-lookup"><span data-stu-id="0edf0-141">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="0edf0-142">Pour résoudre ce problème, mettez à niveau votre version du SDK ou exécutez la commande suivante à la place : `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="0edf0-142">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

* <span data-ttu-id="0edf0-143">Exécute un push de tous les fichiers *. nupkg* même si une réponse de conflit 409 est retournée par un serveur http (S) :</span><span class="sxs-lookup"><span data-stu-id="0edf0-143">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
