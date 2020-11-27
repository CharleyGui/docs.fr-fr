---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: b8496992c7b0694a07ac047ba8537c67fc363c02
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264229"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="62484-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="62484-102">ConfigurationCodeGenerator</span></span>

<span data-ttu-id="62484-103">Le ConfigurationCodeGenerator est un outil que vous pouvez utiliser pour exposer vos implémentations de canal personnalisées au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="62484-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="62484-104">Cela permet aux utilisateurs de votre canal personnalisé de configurer votre canal en utilisant un fichier .config comme ils configureraient une liaison fournie par le système telle que `NetTcpBinding` ou une liaison personnalisée à l'aide de `TcpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="62484-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="62484-105">Lorsque vous écrivez un canal personnalisé et l'exposez au modèle de programmation en utilisant un nouveau `BindingElement` ou une `Binding`, vous devez créer un ensemble de classes pour rendre le `BindingElement` ou la `Binding` configurable à l'aide d'un fichier .config.</span><span class="sxs-lookup"><span data-stu-id="62484-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="62484-106">Vous pouvez utiliser l'outil ConfigurationCodeGenerator pour générer ces classes et améliorer l'expérience de votre client.</span><span class="sxs-lookup"><span data-stu-id="62484-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="62484-107">Pour générer l'outil</span><span class="sxs-lookup"><span data-stu-id="62484-107">To build the tool</span></span>  
  
1. <span data-ttu-id="62484-108">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="62484-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="62484-109">La génération de la solution génère un fichier : ConfigurationCodeGenerator.exe.</span><span class="sxs-lookup"><span data-stu-id="62484-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="62484-110">Le fichier SampleRun. cmd contient un exemple de ligne de commande qui montre comment utiliser cet outil pour générer les classes de l’exemple [transport : UDP](transport-udp.md) .</span><span class="sxs-lookup"><span data-stu-id="62484-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="62484-111">Pour exécuter l'outil</span><span class="sxs-lookup"><span data-stu-id="62484-111">To run the tool</span></span>  
  
1. <span data-ttu-id="62484-112">Dans l'invite de commandes, tapez ce qui suit si vous avez à la fois un type `BindingElement` personnalisé et un type `Binding` personnalisé :</span><span class="sxs-lookup"><span data-stu-id="62484-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="62484-113">Ou tapez ce qui suit si vous avez uniquement un type `BindingElement` personnalisé :</span><span class="sxs-lookup"><span data-stu-id="62484-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="62484-114">Ou tapez ce qui suit si vous avez uniquement un type `Binding` personnalisé :</span><span class="sxs-lookup"><span data-stu-id="62484-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="62484-115">La commande génère trois fichiers .cs pour le `BindingElement` (si vous avez spécifié l'option /be:), cinq fichiers .cs pour la `Binding` standard (si vous avez spécifié l'option /sb:), et un fichier .xml.</span><span class="sxs-lookup"><span data-stu-id="62484-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="62484-116">Si vous avez utilisé l’option /be, l’un des fichiers .cs implémente `BindingElementExtensionSection` pour votre élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="62484-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="62484-117">Ce code expose votre `BindingElement` au système de configuration, afin que d'autres liaisons personnalisées puissent utiliser votre élément de liaison.</span><span class="sxs-lookup"><span data-stu-id="62484-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="62484-118">Les autres fichiers possèdent des classes qui représentent des valeurs par défaut et des constantes.</span><span class="sxs-lookup"><span data-stu-id="62484-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="62484-119">Les fichiers comportent des commentaires `//TODO` pour vous rappeler de mettre à jour les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="62484-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="62484-120">Si vous avez spécifié l'option /sb, deux des fichiers .cs implémentent respectivement un `StandardBindingElement` et un `StandardBindingCollectionElement`, qui expose votre liaison standard au système de configuration.</span><span class="sxs-lookup"><span data-stu-id="62484-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="62484-121">Les autres fichiers possèdent des classes qui représentent des valeurs par défaut et des constantes.</span><span class="sxs-lookup"><span data-stu-id="62484-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="62484-122">Les fichiers comportent des commentaires `//TODO` pour vous rappeler de mettre à jour les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="62484-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="62484-123">Si vous avez spécifié l’option l'/SB :, CodeToAddTo \<*YourStdBinding*> . cs contient du code que vous devez ajouter manuellement dans la classe qui implémente votre liaison standard.</span><span class="sxs-lookup"><span data-stu-id="62484-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="62484-124">Le fichier SampleConfig.xml contient le code de configuration que vous devez ajouter au fichier de configuration qui enregistre les gestionnaires définis à l'étape 1 ou 2 précédente.</span><span class="sxs-lookup"><span data-stu-id="62484-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
