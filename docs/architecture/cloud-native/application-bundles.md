---
title: Lots d’applications Cloud natives
description: Architecture des applications .NET natives Cloud pour Azure | Lots d’applications Cloud natives
ms.date: 06/30/2019
ms.openlocfilehash: 0c67035af08d3c337ff027f3742e1ce8a83f8d0f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183713"
---
# <a name="cloud-native-application-bundles"></a><span data-ttu-id="cd59d-103">Lots d’applications Cloud natives</span><span class="sxs-lookup"><span data-stu-id="cd59d-103">Cloud Native Application Bundles</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cd59d-104">Une propriété clé des applications Cloud natives est qu’elles tirent parti des propriétés du Cloud pour accélérer le développement.</span><span class="sxs-lookup"><span data-stu-id="cd59d-104">A key property of cloud-native applications is that they leverage the properties of the cloud to speed up development.</span></span> <span data-ttu-id="cd59d-105">Cela signifie souvent qu’une application complète utilise différents types de technologies.</span><span class="sxs-lookup"><span data-stu-id="cd59d-105">This often means that a full application uses different kinds of technologies.</span></span> <span data-ttu-id="cd59d-106">Les applications peuvent être livrées dans des conteneurs dockers, certains services peuvent utiliser des Azure Functions, tandis que d’autres peuvent s’exécuter directement sur des machines virtuelles allouées sur des serveurs métalliques de grande taille avec l’accélération GPU matérielle.</span><span class="sxs-lookup"><span data-stu-id="cd59d-106">Applications may be shipped in Docker containers, some services may use Azure Functions while other parts may run directly on virtual machines allocated on large metal servers with hardware GPU acceleration.</span></span> <span data-ttu-id="cd59d-107">Deux applications Cloud natives ne sont pas identiques. il est donc difficile de fournir un mécanisme unique pour les expédier.</span><span class="sxs-lookup"><span data-stu-id="cd59d-107">No two cloud-native applications are the same, so it's been difficult to provide a single mechanism for shipping them.</span></span>

<span data-ttu-id="cd59d-108">Les conteneurs de l’ancrage peuvent s’exécuter sur Kubernetes à l’aide d’un graphique Helm pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="cd59d-108">The Docker containers may run on Kubernetes using a Helm Chart for deployment.</span></span> <span data-ttu-id="cd59d-109">Le Azure Functions peut être alloué à l’aide de modèles Terraform.</span><span class="sxs-lookup"><span data-stu-id="cd59d-109">The Azure Functions may be allocated using Terraform templates.</span></span> <span data-ttu-id="cd59d-110">Enfin, les machines virtuelles peuvent être allouées à l’aide de Terraform mais intégrées à l’aide de Ansible.</span><span class="sxs-lookup"><span data-stu-id="cd59d-110">Finally, the virtual machines may be allocated using Terraform but built out using Ansible.</span></span> <span data-ttu-id="cd59d-111">Il s’agit d’un ensemble de technologies et il n’existe aucun moyen de les empaqueter dans un package raisonnable.</span><span class="sxs-lookup"><span data-stu-id="cd59d-111">This is a whole mess of technologies and there has been no way to package them all together into a reasonable package.</span></span> <span data-ttu-id="cd59d-112">Jusqu'à maintenant.</span><span class="sxs-lookup"><span data-stu-id="cd59d-112">Until now.</span></span>

<span data-ttu-id="cd59d-113">Les offres CNABs (Cloud application native Group) sont un effort conjoint d’un certain nombre d’entreprises à l’esprit de la Communauté, telles que Microsoft, Dockr et HashiCorp, afin de développer une spécification pour empaqueter des applications distribuées.</span><span class="sxs-lookup"><span data-stu-id="cd59d-113">Cloud Native Application Bundles (CNABs) are a joint effort of a number of community-minded companies such as Microsoft, Docker, and HashiCorp to develop a specification to package distributed applications.</span></span>

<span data-ttu-id="cd59d-114">L’effort a été annoncé en décembre de 2018. il reste donc un peu de travail à faire pour exposer l’effort à la communauté supérieure.</span><span class="sxs-lookup"><span data-stu-id="cd59d-114">The effort was announced in December of 2018, so there's still a fair bit of work to do to expose the effort to the greater community.</span></span> <span data-ttu-id="cd59d-115">Toutefois, il existe déjà une [spécification ouverte](https://github.com/deislabs/cnab-spec) et une implémentation de référence appelée [marin](https://duffle.sh/).</span><span class="sxs-lookup"><span data-stu-id="cd59d-115">However, there's already an [open specification](https://github.com/deislabs/cnab-spec) and a reference implementation known as [Duffle](https://duffle.sh/).</span></span> <span data-ttu-id="cd59d-116">Cet outil, qui a été écrit en déplacement, est un effort conjoint entre l’organe d’accueil et Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cd59d-116">This tool, which was written in Go, is a joint effort between Docker and Microsoft.</span></span>

<span data-ttu-id="cd59d-117">Les CNABs peuvent contenir différents types de technologies d’installation.</span><span class="sxs-lookup"><span data-stu-id="cd59d-117">The CNABs can contain different kinds of installation technologies.</span></span> <span data-ttu-id="cd59d-118">Cela permet aux éléments tels que les graphiques Helm, les modèles Terraform et les règles Ansible de coexister dans le même package.</span><span class="sxs-lookup"><span data-stu-id="cd59d-118">This allows things like Helm Charts, Terraform templates, and Ansible Playbooks to coexist in the same package.</span></span> <span data-ttu-id="cd59d-119">Une fois générés, les packages sont autonomes et portables ; elles peuvent être installées à partir d’une clé USB.</span><span class="sxs-lookup"><span data-stu-id="cd59d-119">Once built, the packages are self-contained and portable; they can be installed from a USB stick.</span></span>  <span data-ttu-id="cd59d-120">Les packages sont signés par chiffrement pour s’assurer qu’ils proviennent du tiers qu’ils revendiquent.</span><span class="sxs-lookup"><span data-stu-id="cd59d-120">The packages are cryptographically signed to ensure they originate from the party they claim.</span></span>

<span data-ttu-id="cd59d-121">Le cœur d’un CNAB est un fichier appelé `bundle.json`.</span><span class="sxs-lookup"><span data-stu-id="cd59d-121">The core of a CNAB is a file called `bundle.json`.</span></span> <span data-ttu-id="cd59d-122">Ce fichier définit le contenu du bundle, qu’il s’agisse d’images Terraform ou autres.</span><span class="sxs-lookup"><span data-stu-id="cd59d-122">This file defines the contents of the bundle, be they Terraform or images or anything else.</span></span> <span data-ttu-id="cd59d-123">La figure 11-9 définit un CNAB qui appelle des Terraform.</span><span class="sxs-lookup"><span data-stu-id="cd59d-123">Figure 11-9 defines a CNAB that invokes some Terraform.</span></span> <span data-ttu-id="cd59d-124">Notez, cependant, qu’il définit en fait une image d’appel qui est utilisée pour appeler Terraform.</span><span class="sxs-lookup"><span data-stu-id="cd59d-124">Notice, however, that it actually defines an invocation image that is used to invoke the Terraform.</span></span> <span data-ttu-id="cd59d-125">Lorsqu’il est empaqueté, le fichier de l’ancrage situé dans le répertoire *CNAB* est intégré à une image de l’ancrage, qui sera inclus dans le bundle.</span><span class="sxs-lookup"><span data-stu-id="cd59d-125">When packaged up, the Docker file that is located in the *cnab* directory is built into a Docker image, which will be included in the bundle.</span></span> <span data-ttu-id="cd59d-126">Le fait d’avoir des Terraform installés à l’intérieur d’un conteneur de station d’accueil dans le bundle signifie que les utilisateurs n’ont pas besoin d’installer Terraform sur leur ordinateur pour exécuter le regroupement.</span><span class="sxs-lookup"><span data-stu-id="cd59d-126">Having Terraform installed inside a Docker container in the bundle means that users don't need to have Terraform installed on their machine to run the bundling.</span></span>

```json
{
    "name": "terraform",
    "version": "0.1.0",
    "schemaVersion": "v1.0.0-WD",
    "parameters": {
        "backend": {
            "type": "boolean",
            "defaultValue": false,
            "destination": {
                "env": "TF_VAR_backend"
            }
        }
    },
    "invocationImages": [
        {
        "imageType": "docker",
        "image": "cnab/terraform:latest"
        }
    ],
    "credentials": {
        "tenant_id": {
            "env": "TF_VAR_tenant_id"
        },
        "client_id": {
            "env": "TF_VAR_client_id"
        },
        "client_secret": {
            "env": "TF_VAR_client_secret"
        },
        "subscription_id": {
            "env": "TF_VAR_subscription_id"
        },
        "ssh_authorized_key": {
            "env": "TF_VAR_ssh_authorized_key"
        }
    },
    "actions": {
        "status": {
            "modifies": true
        }
    }
}
```

<span data-ttu-id="cd59d-127">**Figure 11-13** : exemple de fichier Terraform</span><span class="sxs-lookup"><span data-stu-id="cd59d-127">**Figure 11-13** - An example Terraform file</span></span>

<span data-ttu-id="cd59d-128">Définit `bundle.json` également un ensemble de paramètres qui sont passés dans le Terraform.</span><span class="sxs-lookup"><span data-stu-id="cd59d-128">The `bundle.json` also defines a set of parameters that are passed down into the Terraform.</span></span> <span data-ttu-id="cd59d-129">Le paramétrage du Bundle permet une installation dans différents environnements.</span><span class="sxs-lookup"><span data-stu-id="cd59d-129">Parameterization of the bundle allows for installation in a variety of different environments.</span></span>

<span data-ttu-id="cd59d-130">Le format CNAB est également flexible, ce qui lui permet d’être utilisé sur n’importe quel Cloud.</span><span class="sxs-lookup"><span data-stu-id="cd59d-130">The CNAB format is also flexible, allowing it to be used against any cloud.</span></span> <span data-ttu-id="cd59d-131">Il peut même être utilisé avec des solutions locales telles que [OpenStack](https://www.openstack.org/).</span><span class="sxs-lookup"><span data-stu-id="cd59d-131">It can even be used against on-premises solutions such as [OpenStack](https://www.openstack.org/).</span></span>

## <a name="devops-decisions"></a><span data-ttu-id="cd59d-132">Décisions DevOps</span><span class="sxs-lookup"><span data-stu-id="cd59d-132">DevOps Decisions</span></span>

<span data-ttu-id="cd59d-133">Il y a tellement de nombreux outils exceptionnels dans l’espace DevOps ces journées et encore plus fantastiques de livres et de documents sur la manière de mener à bien.</span><span class="sxs-lookup"><span data-stu-id="cd59d-133">There are so many great tools in the DevOps space these days and even more fantastic books and papers on how to succeed.</span></span> <span data-ttu-id="cd59d-134">Un livre favori pour la prise en main du parcours DevOps est [le projet Phoenix](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), qui suit la transformation d’une société fictive de NoOps en DevOps.</span><span class="sxs-lookup"><span data-stu-id="cd59d-134">A favorite book to get started on the DevOps journey is [The Phoenix Project](https://www.oreilly.com/library/view/the-phoenix-project/9781457191350/), which follows the transformation of a fictional company from NoOps to DevOps.</span></span> <span data-ttu-id="cd59d-135">Une chose est pour certains : DevOps n’est plus une « belle à avoir » lors du déploiement d’applications natives du Cloud.</span><span class="sxs-lookup"><span data-stu-id="cd59d-135">One thing is for certain: DevOps is no longer a "nice to have" when deploying complex, Cloud Native Applications.</span></span> <span data-ttu-id="cd59d-136">Elle est obligatoire et doit être planifiée et Resource au début de tout projet.</span><span class="sxs-lookup"><span data-stu-id="cd59d-136">It's a requirement and should be planned for and resourced at the start of any project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="cd59d-137">Précédent</span><span class="sxs-lookup"><span data-stu-id="cd59d-137">Previous</span></span>](infrastructure-as-code.md)
