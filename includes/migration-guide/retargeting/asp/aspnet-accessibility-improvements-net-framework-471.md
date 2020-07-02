---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614459"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a><span data-ttu-id="4aae6-101">Améliorations de l’accessibilité ASP.NET dans .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="4aae6-101">ASP.NET Accessibility Improvements in .NET Framework 4.7.1</span></span>

#### <a name="details"></a><span data-ttu-id="4aae6-102">Détails</span><span class="sxs-lookup"><span data-stu-id="4aae6-102">Details</span></span>

<span data-ttu-id="4aae6-103">À compter de .NET Framework 4.7.1, ASP.NET a amélioré le fonctionnement des contrôles web ASP.NET avec la technologie d’accessibilité de Visual Studio pour une meilleure prise en charge des clients ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4aae6-103">Starting with the .NET Framework 4.7.1, ASP.NET has improved how ASP.NET Web Controls work with accessibility technology in Visual Studio to better support ASP.NET customers.</span></span>  <span data-ttu-id="4aae6-104">Citons notamment les changements suivants :</span><span class="sxs-lookup"><span data-stu-id="4aae6-104">These include the following changes:</span></span>

- <span data-ttu-id="4aae6-105">Changements visant à implémenter les modèles d’accessibilité de l’interface utilisateur manquants dans les contrôles, comme la boîte de dialogue Ajouter un champ de l’Assistant de la vue Détails ou la boîte de dialogue Configurer ListView de l’Assistant ListView.</span><span class="sxs-lookup"><span data-stu-id="4aae6-105">Changes to implement missing UI accessibility patterns in controls, like the Add Field dialog in the Details View wizard, or the Configure ListView dialog of the ListView wizard.</span></span>
- <span data-ttu-id="4aae6-106">Changements visant à améliorer l’affichage en mode de contraste élevé, comme l’éditeur de champs du pagineur de données.</span><span class="sxs-lookup"><span data-stu-id="4aae6-106">Changes to improve the display in High Contrast mode, like the Data Pager Fields Editor.</span></span>
- <span data-ttu-id="4aae6-107">Changements visant à améliorer les expériences de navigation au clavier pour les contrôles, comme la boîte de dialogue Champs de l’Assistant Modifier les champs pager du contrôle DataPager, la boîte de dialogue Configurer ObjectContext ou la boîte de dialogue Configurer la sélection de données de l’Assistant Configurer la source de données.</span><span class="sxs-lookup"><span data-stu-id="4aae6-107">Changes to improve the keyboard navigation experiences for controls, like the Fields dialog in the Edit Pager Fields wizard of the DataPager control, the Configure ObjectContext dialog, or the Configure Data Selection dialog of the Configure Data Source wizard.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4aae6-108">Suggestion</span><span class="sxs-lookup"><span data-stu-id="4aae6-108">Suggestion</span></span>

<span data-ttu-id="4aae6-109">**Comment accepter ou refuser ces changements** Pour que le concepteur Visual Studio tire parti de ces changements, il doit s’exécuter sur .NET Framework 4.7.1 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="4aae6-109">**How to opt in or out of these changes** In order for the Visual Studio Designer to benefit from these changes, it must run on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="4aae6-110">Pour que l’application web tire parti de ces changements, procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="4aae6-110">The web application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="4aae6-111">Installez Visual Studio 2017 15.3 ou une version ultérieure, qui prend en charge les nouvelles fonctionnalités d’accessibilité avec le commutateur AppContext suivant par défaut.</span><span class="sxs-lookup"><span data-stu-id="4aae6-111">Install Visual Studio 2017 15.3 or later, which supports the new accessibility features with the following AppContext Switch by default.</span></span>
- <span data-ttu-id="4aae6-112">Refusez les comportements d’accessibilité hérités en ajoutant le commutateur AppContext `Switch.UseLegacyAccessibilityFeatures` à la section `<runtime>` du fichier devenv.exe.config et en lui affectant la valeur `false`, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4aae6-112">Opt out of the legacy accessibility behaviors by adding the `Switch.UseLegacyAccessibilityFeatures` AppContext switch to the `<runtime>` section in the devenv.exe.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

<span data-ttu-id="4aae6-113">Si votre application cible .NET Framework 4.7.1 ou une version ultérieure et que vous souhaitez conserver le comportement d’accessibilité hérité, choisissez d’utiliser les fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="4aae6-113">Applications that target the .NET Framework 4.7.1 or later and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="4aae6-114">Nom</span><span class="sxs-lookup"><span data-stu-id="4aae6-114">Name</span></span>    | <span data-ttu-id="4aae6-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="4aae6-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4aae6-116">Étendue</span><span class="sxs-lookup"><span data-stu-id="4aae6-116">Scope</span></span>   | <span data-ttu-id="4aae6-117">Secondaire</span><span class="sxs-lookup"><span data-stu-id="4aae6-117">Minor</span></span>       |
| <span data-ttu-id="4aae6-118">Version</span><span class="sxs-lookup"><span data-stu-id="4aae6-118">Version</span></span> | <span data-ttu-id="4aae6-119">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4aae6-119">4.7.1</span></span>       |
| <span data-ttu-id="4aae6-120">Type</span><span class="sxs-lookup"><span data-stu-id="4aae6-120">Type</span></span>    | <span data-ttu-id="4aae6-121">Reciblage</span><span class="sxs-lookup"><span data-stu-id="4aae6-121">Retargeting</span></span> |
