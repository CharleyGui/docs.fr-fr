---
title: Configuration de l’exécution
description: Découvrez comment configurer des applications .NET Core à l’aide des paramètres de configuration de l’exécution.
ms.date: 11/13/2019
ms.openlocfilehash: 2665026347e94d26026821beb2bfcf8441f755f6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801919"
---
# <a name="net-core-run-time-configuration-settings"></a><span data-ttu-id="1b8d7-103">Paramètres de configuration du Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="1b8d7-103">.NET Core run-time configuration settings</span></span>

<span data-ttu-id="1b8d7-104">.NET Core prend en charge l’utilisation de fichiers de configuration et de variables d’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-104">.NET Core supports the use of configuration files and environment variables to configure the behavior of .NET Core applications at run time.</span></span> <span data-ttu-id="1b8d7-105">La configuration au moment de l’exécution est une option attrayante dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="1b8d7-105">Run-time configuration is an attractive option if:</span></span>

- <span data-ttu-id="1b8d7-106">Vous ne possédez pas ou ne contrôlez pas le code source d’une application. par conséquent, vous ne pouvez pas le configurer par programme.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-106">You don't own or control the source code for an application and therefore are unable to configure it programmatically.</span></span>

- <span data-ttu-id="1b8d7-107">Plusieurs instances de votre application s’exécutent en même temps sur un système unique et vous souhaitez configurer chacune d’elles pour obtenir des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-107">Multiple instances of your application run at the same time on a single system, and you want to configure each for optimum performance.</span></span>

> [!NOTE]
> <span data-ttu-id="1b8d7-108">Cette documentation est un travail en cours.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-108">This documentation is a work in progress.</span></span> <span data-ttu-id="1b8d7-109">Si vous remarquez que les informations présentées ici sont incomplètes ou inexactes, vous pouvez soit [ouvrir un problème](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettre une demande de tirage](https://github.com/dotnet/docs/pulls) pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-109">If you notice that the information presented here is either incomplete or inaccurate, either [open an issue](https://github.com/dotnet/docs/issues) to let us know about it, or [submit a pull request](https://github.com/dotnet/docs/pulls) to address the issue.</span></span> <span data-ttu-id="1b8d7-110">Pour plus d’informations sur l’envoi de requêtes de tirage pour le dépôt dotnet/docs, consultez le [Guide du contributeur](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="1b8d7-110">For information on submitting pull requests for the dotnet/docs repository, see the [contributor's guide](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>

<span data-ttu-id="1b8d7-111">.NET Core fournit les mécanismes suivants pour configurer des applications au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="1b8d7-111">.NET Core provides the following mechanisms for configuring applications at run time:</span></span>

- <span data-ttu-id="1b8d7-112">Le [fichier runtimeconfig. JSON](#runtimeconfigjson)</span><span class="sxs-lookup"><span data-stu-id="1b8d7-112">The [runtimeconfig.json file](#runtimeconfigjson)</span></span>

- [<span data-ttu-id="1b8d7-113">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="1b8d7-113">Environment variables</span></span>](#environment-variables)

<span data-ttu-id="1b8d7-114">Les Articles de cette section de la documentation incluent sont organisés par catégorie, par exemple, débogage et garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-114">The articles in this section of the documentation include are organized by category, for example, debugging and garbage collection.</span></span> <span data-ttu-id="1b8d7-115">Le cas échéant, les options de configuration s’affichent pour *runtimeconfig. JSON* (.net Core uniquement), *app. config* (.NET Framework uniquement) et les variables d’environnement.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-115">Where applicable, configuration options are shown for *runtimeconfig.json* (.NET Core only), *app.config* (.NET Framework only), and environment variables.</span></span>

## <a name="runtimeconfigjson"></a><span data-ttu-id="1b8d7-116">runtimeconfig. JSON</span><span class="sxs-lookup"><span data-stu-id="1b8d7-116">runtimeconfig.json</span></span>

<span data-ttu-id="1b8d7-117">Spécifiez les options de configuration au moment de l’exécution dans la section **configProperties** du fichier *runtimeconfig. JSON* de l’application.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-117">Specify run-time configuration options in the **configProperties** section of the app's *runtimeconfig.json* file.</span></span> <span data-ttu-id="1b8d7-118">Cette section se présente sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="1b8d7-118">This section has the form:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

<span data-ttu-id="1b8d7-119">Voici un exemple de fichier :</span><span class="sxs-lookup"><span data-stu-id="1b8d7-119">Here is an example file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

<span data-ttu-id="1b8d7-120">Le fichier *runtimeconfig. JSON* est automatiquement créé dans le répertoire de build par la commande [dotnet Build](../tools/dotnet-build.md) .</span><span class="sxs-lookup"><span data-stu-id="1b8d7-120">The *runtimeconfig.json* file is automatically created in the build directory by the [dotnet build](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="1b8d7-121">Elle est également créée lorsque vous sélectionnez l’option de menu **générer** dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-121">It's also created when you select the **Build** menu option in Visual Studio.</span></span> <span data-ttu-id="1b8d7-122">Vous pouvez ensuite modifier le fichier une fois qu’il a été créé.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-122">You can then edit the file once it's created.</span></span>

<span data-ttu-id="1b8d7-123">Certaines valeurs de configuration peuvent également être définies par programmation en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-123">Some configuration values can also be set programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="1b8d7-124">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="1b8d7-124">Environment variables</span></span>

<span data-ttu-id="1b8d7-125">Les variables d’environnement peuvent être utilisées pour fournir des informations de configuration au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-125">Environment variables can be used to supply some run-time configuration information.</span></span> <span data-ttu-id="1b8d7-126">Les boutons de configuration spécifiés en tant que variables d’environnement ont généralement le préfixe **COMPlus_** .</span><span class="sxs-lookup"><span data-stu-id="1b8d7-126">Configuration knobs specified as environment variables generally have the prefix **COMPlus_**.</span></span>

<span data-ttu-id="1b8d7-127">Vous pouvez définir des variables d’environnement à partir du panneau de configuration Windows, à partir de la ligne de commande ou par programme, en appelant la méthode <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> sur les systèmes Windows et UNIX.</span><span class="sxs-lookup"><span data-stu-id="1b8d7-127">You can define environment variables from the Windows Control Panel, at the command line, or programmatically by calling the <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> method on both Windows and Unix-based systems.</span></span>

<span data-ttu-id="1b8d7-128">Les exemples suivants montrent comment définir une variable d’environnement sur la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="1b8d7-128">The following examples show how to set an environment variable at the command line:</span></span>

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
