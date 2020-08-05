---
title: Commande dotnet nuget push
description: La commande dotnet nuget push exécute un envoi (push) d’un package sur le serveur et le publie.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 50a4a542c2d192bfbd927845489d04fd1b6c6cf3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555121"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="ccc2e-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="ccc2e-103">dotnet nuget push</span></span>

<span data-ttu-id="ccc2e-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="ccc2e-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ccc2e-105">Nom</span><span class="sxs-lookup"><span data-stu-id="ccc2e-105">Name</span></span>

<span data-ttu-id="ccc2e-106">`dotnet nuget push` - Exécute un push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ccc2e-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="ccc2e-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols true]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="ccc2e-108">Description</span><span class="sxs-lookup"><span data-stu-id="ccc2e-108">Description</span></span>

<span data-ttu-id="ccc2e-109">La commande `dotnet nuget push` exécute un push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="ccc2e-110">La commande push utilise les informations serveur et d’identification trouvées dans le fichier ou la chaîne de fichiers de configuration NuGet du système.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="ccc2e-111">Pour plus d’informations sur les fichiers de configuration, consultez [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior) (Configuration du comportement de NuGet ).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="ccc2e-112">La configuration par défaut de NuGet est obtenue en chargeant *%AppData%\NuGet\NuGet.config* (Windows) ou *$HOME/.local/share* (Linux/macOS), puis en chargeant tout fichier *nuget.config* ou *.nuget\nuget.config* à partir de la racine du lecteur jusqu’au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="ccc2e-113">La commande exécute un push d’un package existant.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-113">The command pushes an existing package.</span></span> <span data-ttu-id="ccc2e-114">Il ne crée pas de package.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-114">It doesn't create a package.</span></span> <span data-ttu-id="ccc2e-115">Pour créer un package, utilisez [`dotnet pack`](dotnet-pack.md) .</span><span class="sxs-lookup"><span data-stu-id="ccc2e-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="ccc2e-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="ccc2e-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="ccc2e-117">Spécifie le chemin de fichier au package devant faire l’objet d’un envoi (push).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="ccc2e-118">Options</span><span class="sxs-lookup"><span data-stu-id="ccc2e-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="ccc2e-119">Désactive la mise en mémoire tampon pendant le transfert push vers un serveur HTTP(S) afin de réduire l’utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="ccc2e-120">Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ccc2e-121">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="ccc2e-122">Autorise la commande pour bloquer et exige une action manuelle pour des opérations comme l'authentification.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="ccc2e-123">Option disponible à partir du SDK .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="ccc2e-124">Clé d’API pour le serveur.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-124">The API key for the server.</span></span>

- **`-n|--no-symbols true`**

  <span data-ttu-id="ccc2e-125">N’envoie pas les symboles (même s’ils sont présents).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="ccc2e-126">N’ajoute pas « api/v2/package » à l’URL source.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="ccc2e-127">Option disponible à partir du kit SDK .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="ccc2e-128">Spécifie l’URL du serveur.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-128">Specifies the server URL.</span></span> <span data-ttu-id="ccc2e-129">Cette option est obligatoire, sauf si la valeur de configuration de `DefaultPushSource` est définie dans le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-129">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="ccc2e-130">Lors du push de plusieurs packages sur un serveur HTTP (S), traite toute réponse de conflit 409 comme un avertissement afin que l’envoi puisse continuer.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-130">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="ccc2e-131">Disponible depuis le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-131">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="ccc2e-132">Clé d’API pour le serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-132">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="ccc2e-133">Spécifie l’URL du serveur de symboles.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-133">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="ccc2e-134">Spécifie le délai d’attente, en secondes, pour effectuer un push vers un serveur.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-134">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="ccc2e-135">La valeur par défaut est 300 secondes (5 minutes).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-135">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="ccc2e-136">Si vous spécifiez 0 (zéro seconde), la valeur par défaut s’applique.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-136">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="ccc2e-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="ccc2e-137">Examples</span></span>

- <span data-ttu-id="ccc2e-138">Envoyez *foo. nupkg* à la source push par défaut, en spécifiant une clé API :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-138">Push *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="ccc2e-139">Appuyez sur *foo. nupkg* sur le serveur NuGet officiel, en spécifiant une clé API :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-139">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="ccc2e-140">Envoyez (push) *foo.nupkg* à la source de push personnalisée `https://customsource`, en spécifiant une clé API :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-140">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="ccc2e-141">Envoyez *foo. nupkg* vers la source de push par défaut :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-141">Push *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="ccc2e-142">Envoyer *foo. Symbols. nupkg* vers la source de symboles par défaut :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-142">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="ccc2e-143">Envoyez *foo. nupkg* à la source de push par défaut, en spécifiant un délai de 360 seconde :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-143">Push *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="ccc2e-144">Envoyer tous les fichiers *. nupkg* du répertoire actif vers la source de push par défaut :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-144">Push all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg"
  ```

  > [!NOTE]
  > <span data-ttu-id="ccc2e-145">Si cette commande ne fonctionne pas, cela peut être dû à un bogue qui existait dans les versions antérieures du SDK (Kit SDK .NET Core 2.1 et versions antérieures).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-145">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="ccc2e-146">Pour résoudre ce problème, mettez à niveau votre version du SDK ou exécutez la commande suivante à la place : `dotnet nuget push "**/*.nupkg"`</span><span class="sxs-lookup"><span data-stu-id="ccc2e-146">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push "**/*.nupkg"`</span></span>
  
  > [!NOTE]
  > <span data-ttu-id="ccc2e-147">Les guillemets englobantes sont requis pour les shells tels que bash qui effectuent des globbing de fichier.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-147">The enclosing quotes are required for shells such as bash that perform file globbing.</span></span> <span data-ttu-id="ccc2e-148">Pour plus d’informations, consultez [NuGet/page de démarrage # 4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-148">For more information, see [NuGet/Home#4393](https://github.com/NuGet/Home/issues/4393#issuecomment-667618120).</span></span>

- <span data-ttu-id="ccc2e-149">Envoyer tous les fichiers *. nupkg* même si une réponse de conflit 409 est retournée par un serveur http (S) :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-149">Push all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg" --skip-duplicate
  ```

- <span data-ttu-id="ccc2e-150">Envoyer tous les fichiers *. nupkg* du répertoire actif vers un répertoire de flux local :</span><span class="sxs-lookup"><span data-stu-id="ccc2e-150">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push "*.nupkg" -s c:\mydir
  ```

  <span data-ttu-id="ccc2e-151">Cette commande ne stocke pas les packages dans une structure de dossiers hiérarchique, ce qui est recommandé pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="ccc2e-151">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="ccc2e-152">Pour plus d’informations, consultez [flux locaux](/nuget/hosting-packages/local-feeds).</span><span class="sxs-lookup"><span data-stu-id="ccc2e-152">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
