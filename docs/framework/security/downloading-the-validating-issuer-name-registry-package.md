---
title: Téléchargement du package de validation du registre des noms d'émetteurs
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 5684844f1db33b075df099b3026d9d0c1061199f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631847"
---
# <a name="download-the-validating-issuer-name-registry-package"></a><span data-ttu-id="28d3c-102">Télécharger le Package de Registre de nom émetteur lors de la validation</span><span class="sxs-lookup"><span data-stu-id="28d3c-102">Download the Validating Issuer Name Registry Package</span></span>

<span data-ttu-id="28d3c-103">Cette rubrique explique comment télécharger et utiliser le Registre des noms d’émetteurs de validation (VINR, Validating Issuer Name Registry) dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="28d3c-103">This topic discusses how to download and use the Validating Issuer Name Registry (VINR) in your project.</span></span>

<span data-ttu-id="28d3c-104">Le Registre VINR est disponible sous forme de package NuGet, qui ajoute les assemblys et les références nécessaires à votre projet.</span><span class="sxs-lookup"><span data-stu-id="28d3c-104">The VINR is available as a NuGet package, which adds the necessary assemblies and references to your project.</span></span> <span data-ttu-id="28d3c-105">Si vous n’avez pas encore installé NuGet, accédez à [nuget.org](https://nuget.org) pour l’installer.</span><span class="sxs-lookup"><span data-stu-id="28d3c-105">If you do not already have NuGet installed, go to [nuget.org](https://nuget.org) to install it.</span></span> <span data-ttu-id="28d3c-106">Vous pouvez consulter l’historique de contrôle de version pour l’extension en visitant sa page sur NuGet : [Validation du Registre de nom de l’émetteur sur NuGet de Microsoft](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span><span class="sxs-lookup"><span data-stu-id="28d3c-106">You can see the versioning history for the extension by visiting its page on NuGet: [Microsoft Validating Issuer Name Registry on NuGet](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)</span></span>

## <a name="use-the-package-manager-gui"></a><span data-ttu-id="28d3c-107">Utiliser l’interface utilisateur graphique du Gestionnaire de Package</span><span class="sxs-lookup"><span data-stu-id="28d3c-107">Use the Package Manager GUI</span></span>

1. <span data-ttu-id="28d3c-108">Dans Visual Studio, cliquez sur votre projet dans l’**Explorateur de solutions**, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="28d3c-108">In Visual Studio, right-click your project in **Solution Explorer**, and then select **Manage NuGet Packages**.</span></span>

2. <span data-ttu-id="28d3c-109">Dans la fenêtre **Gérer les packages NuGet**, cliquez sur la zone de recherche et tapez `ValidatingIssuerNameRegistry`, puis appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="28d3c-109">In the **Manage NuGet Packages** window, click the search box and enter `ValidatingIssuerNameRegistry` and press **Enter**.</span></span>

3. <span data-ttu-id="28d3c-110">Dans le volet de résultats, cliquez sur le bouton **Installer** pour le premier résultat.</span><span class="sxs-lookup"><span data-stu-id="28d3c-110">From the results pane, click the **Install** button for the first result.</span></span>

4. <span data-ttu-id="28d3c-111">Le téléchargement du package commence.</span><span class="sxs-lookup"><span data-stu-id="28d3c-111">The package will begin downloading.</span></span> <span data-ttu-id="28d3c-112">Avant l’ajout du package à votre projet, la boîte de dialogue d’acceptation de licence s’affiche.</span><span class="sxs-lookup"><span data-stu-id="28d3c-112">Before it is added to your project, the License Acceptance dialog will appear.</span></span> <span data-ttu-id="28d3c-113">Si vous êtes d’accord avec les termes du contrat de licence, cliquez sur **Accepter**.</span><span class="sxs-lookup"><span data-stu-id="28d3c-113">If you agree to the license terms, click **I Accept**.</span></span>

5. <span data-ttu-id="28d3c-114">Les assemblys VINR les plus récents seront téléchargés et ajoutés à votre projet.</span><span class="sxs-lookup"><span data-stu-id="28d3c-114">The latest VINR assemblies will be downloaded and added to your project.</span></span>

## <a name="use-the-package-manager-console"></a><span data-ttu-id="28d3c-115">Utilisez la Console du Gestionnaire de Package</span><span class="sxs-lookup"><span data-stu-id="28d3c-115">Use the Package Manager Console</span></span>

1. <span data-ttu-id="28d3c-116">Dans Visual Studio, cliquez sur **outils** > **Gestionnaire de Package NuGet** > **Console du Gestionnaire de Package**.</span><span class="sxs-lookup"><span data-stu-id="28d3c-116">In Visual Studio, click **Tools** > **NuGet Package Manager** > **Package Manager Console**.</span></span>

2. <span data-ttu-id="28d3c-117">La **Console du Gestionnaire de package** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="28d3c-117">The **Package Manager Console** appears.</span></span> <span data-ttu-id="28d3c-118">Tapez le texte suivant et appuyez sur **Entrée** :</span><span class="sxs-lookup"><span data-stu-id="28d3c-118">Enter the following text and press **Enter**:</span></span>

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. <span data-ttu-id="28d3c-119">Les assemblys VINR les plus récents seront téléchargés et ajoutés à votre projet.</span><span class="sxs-lookup"><span data-stu-id="28d3c-119">The latest VINR assemblies will be downloaded and added to your project.</span></span>
