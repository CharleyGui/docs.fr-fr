---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614548"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a><span data-ttu-id="d91a5-101">Amélioration de l’accessibilité pour certains outils du SDK .NET</span><span class="sxs-lookup"><span data-stu-id="d91a5-101">Improved accessibility for some .NET SDK tools</span></span>

#### <a name="details"></a><span data-ttu-id="d91a5-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d91a5-102">Details</span></span>

<span data-ttu-id="d91a5-103">Dans le kit .NET Framework SDK 4.7.1, les outils SvcConfigEditor.exe et SvcTraceViewer.exe ont été améliorés en corrigeant différents problèmes d’accessibilité.</span><span class="sxs-lookup"><span data-stu-id="d91a5-103">In the .NET Framework SDK 4.7.1, the SvcConfigEditor.exe and SvcTraceViewer.exe tools have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="d91a5-104">La plupart étaient des petits problèmes comme un nom non défini ou certains modèles d’automatisation de l’interface utilisateur non implémentés correctement.</span><span class="sxs-lookup"><span data-stu-id="d91a5-104">Most of these were small issues like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="d91a5-105">Si de nombreux utilisateurs n’ont pas conscience de ces valeurs incorrectes, les clients qui utilisent des technologies d’assistance comme les lecteurs d’écran trouveront ces outils du kit de développement logiciel (SDK) plus accessibles.</span><span class="sxs-lookup"><span data-stu-id="d91a5-105">While many users wouldn't be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> <span data-ttu-id="d91a5-106">Il est évident que ces correctifs changent certains comportements précédents, comme l’ordre de focus clavier. Pour obtenir tous les correctifs liés à l’accessibilité dans ces outils, vous pouvez ajouter ce qui suit à votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="d91a5-106">Certainly, these fixes change some previous behaviors, like keyboard focus order.In order to get all the accessibility fixes in these tools, you can the following to your app.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| <span data-ttu-id="d91a5-107">Nom</span><span class="sxs-lookup"><span data-stu-id="d91a5-107">Name</span></span>    | <span data-ttu-id="d91a5-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="d91a5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d91a5-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="d91a5-109">Scope</span></span>   | <span data-ttu-id="d91a5-110">Edge</span><span class="sxs-lookup"><span data-stu-id="d91a5-110">Edge</span></span>        |
| <span data-ttu-id="d91a5-111">Version</span><span class="sxs-lookup"><span data-stu-id="d91a5-111">Version</span></span> | <span data-ttu-id="d91a5-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="d91a5-112">4.7.1</span></span>       |
| <span data-ttu-id="d91a5-113">Type</span><span class="sxs-lookup"><span data-stu-id="d91a5-113">Type</span></span>    | <span data-ttu-id="d91a5-114">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d91a5-114">Retargeting</span></span> |
