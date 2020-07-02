---
ms.openlocfilehash: f980c8029375074889505a8eb7e8a65aaa8d74e4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614518"
---
### <a name="resgen-refuses-to-load-content-from-the-web"></a><span data-ttu-id="83800-101">Resgen refuse de charger le contenu à partir du Web</span><span class="sxs-lookup"><span data-stu-id="83800-101">Resgen refuses to load content from the web</span></span>

#### <a name="details"></a><span data-ttu-id="83800-102">Détails</span><span class="sxs-lookup"><span data-stu-id="83800-102">Details</span></span>

<span data-ttu-id="83800-103">les fichiers. resx peuvent contenir une entrée au format binaire.</span><span class="sxs-lookup"><span data-stu-id="83800-103">.resx files may contain binary formatted input.</span></span> <span data-ttu-id="83800-104">Si vous tentez d’utiliser Resgen pour charger un fichier qui a été téléchargé à partir d’un emplacement non approuvé, il ne parviendra pas à charger l’entrée par défaut.</span><span class="sxs-lookup"><span data-stu-id="83800-104">If you attempt to use resgen to load a file that was downloaded from an untrusted location, it will fail to load the input by default.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="83800-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="83800-105">Suggestion</span></span>

<span data-ttu-id="83800-106">Les utilisateurs Resgen qui requièrent le chargement d’une entrée au format binaire à partir d’emplacements non approuvés peuvent supprimer la marque du Web du fichier d’entrée ou appliquer la particularité de l’annulation. Ajoutez le paramètre de Registre suivant pour appliquer la particularité de l’annulation de l’ordinateur : [HKEY_LOCAL_MACHINE \Software\Microsoft.netframework\sdk] &quot; AllowProcessOfUntrustedResourceFiles &quot; = &quot; true&quot;</span><span class="sxs-lookup"><span data-stu-id="83800-106">Resgen users who require loading binary formatted input from untrusted locations can either remove the mark of the web from the input file or apply the opt-out quirk.Add the following registry setting to apply the machine wide opt-out quirk: [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework\SDK] &quot;AllowProcessOfUntrustedResourceFiles&quot;=&quot;true&quot;</span></span>

| <span data-ttu-id="83800-107">Nom</span><span class="sxs-lookup"><span data-stu-id="83800-107">Name</span></span>    | <span data-ttu-id="83800-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="83800-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="83800-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="83800-109">Scope</span></span>   | <span data-ttu-id="83800-110">Edge</span><span class="sxs-lookup"><span data-stu-id="83800-110">Edge</span></span>        |
| <span data-ttu-id="83800-111">Version</span><span class="sxs-lookup"><span data-stu-id="83800-111">Version</span></span> | <span data-ttu-id="83800-112">4.7.2</span><span class="sxs-lookup"><span data-stu-id="83800-112">4.7.2</span></span>       |
| <span data-ttu-id="83800-113">Type</span><span class="sxs-lookup"><span data-stu-id="83800-113">Type</span></span>    | <span data-ttu-id="83800-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="83800-114">Retargeting</span></span> |
