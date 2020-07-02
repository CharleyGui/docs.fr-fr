---
ms.openlocfilehash: 97299ddb9bee89c792ddb3d2b9c37516180996f7
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614569"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a><span data-ttu-id="d7ef0-101">La propriété ContextMenuStrip.SourceControl contient un contrôle valide dans le cas des ToolStripMenuItems imbriqués</span><span class="sxs-lookup"><span data-stu-id="d7ef0-101">ContextMenuStrip.SourceControl property contains a valid control in the case of nested ToolStripMenuItems</span></span>

#### <a name="details"></a><span data-ttu-id="d7ef0-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d7ef0-102">Details</span></span>

<span data-ttu-id="d7ef0-103">Dans .NET Framework 4.7.1 et versions antérieures, la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> retourne la valeur null quand l’utilisateur ouvre le menu à partir de contrôles <xref:System.Windows.Forms.ToolStripMenuItem> imbriqués.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-103">In the .NET Framework 4.7.1 and previous versions, the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property incorrectly returns null when the user opens the menu from nested <xref:System.Windows.Forms.ToolStripMenuItem> controls.</span></span> <span data-ttu-id="d7ef0-104">Dans .NET Framework 4.7.2 et versions ultérieures, la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> est toujours définie sur le contrôle de code source réel.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-104">In the .NET Framework 4.7.2 and later, <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> property is always set to the actual source control.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d7ef0-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d7ef0-105">Suggestion</span></span>

<span data-ttu-id="d7ef0-106">**Comment accepter ou refuser ces modifications** Pour qu’une application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.2 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-106">**How to opt in or out of these changes** In order for an application to benefit from these changes, it must run on the .NET Framework 4.7.2 or later.</span></span> <span data-ttu-id="d7ef0-107">Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7ef0-107">The application can benefit from these changes in either of the following ways:</span></span>

- <span data-ttu-id="d7ef0-108">Faites-lui cibler .NET Framework 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-108">It targets the .NET Framework 4.7.2.</span></span> <span data-ttu-id="d7ef0-109">Ce changement est activé par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-109">This change is enabled by default on Windows Forms applications that target the .NET Framework 4.7.2 or later.</span></span>
- <span data-ttu-id="d7ef0-110">Faites-lui cibler .NET Framework version 4.7.1 ou antérieure et refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la section `<runtime>` du fichier app.config et en lui affectant la valeur `false`, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-110">It targets the .NET Framework 4.7.1 or an earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext Switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app.config file and setting it to `false`, as the following example shows.</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

<span data-ttu-id="d7ef0-111">Si votre application cible .NET Framework 4.7.2 ou une version ultérieure et que vous souhaitez conserver le comportement hérité, choisissez d’utiliser la valeur de contrôle de code source héritée en affectant explicitement à ce commutateur AppContext la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="d7ef0-111">Applications that target the .NET Framework 4.7.2 or later, and want to preserve the legacy behavior can opt in to the use of the legacy source control value by explicitly setting this AppContext switch to `true`.</span></span>

| <span data-ttu-id="d7ef0-112">Nom</span><span class="sxs-lookup"><span data-stu-id="d7ef0-112">Name</span></span>    | <span data-ttu-id="d7ef0-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="d7ef0-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d7ef0-114">Étendue</span><span class="sxs-lookup"><span data-stu-id="d7ef0-114">Scope</span></span>   | <span data-ttu-id="d7ef0-115">Edge</span><span class="sxs-lookup"><span data-stu-id="d7ef0-115">Edge</span></span>        |
| <span data-ttu-id="d7ef0-116">Version</span><span class="sxs-lookup"><span data-stu-id="d7ef0-116">Version</span></span> | <span data-ttu-id="d7ef0-117">4.7.2</span><span class="sxs-lookup"><span data-stu-id="d7ef0-117">4.7.2</span></span>       |
| <span data-ttu-id="d7ef0-118">Type</span><span class="sxs-lookup"><span data-stu-id="d7ef0-118">Type</span></span>    | <span data-ttu-id="d7ef0-119">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d7ef0-119">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="d7ef0-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="d7ef0-120">Affected APIs</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
