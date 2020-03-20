---
ms.openlocfilehash: 8db115a46df3fcea103e8fa6896542d0116aa256
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804669"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="d41f5-101">VB.NET ne prend plus en charge la qualification partielle des espaces de noms pour les API System.Windows</span><span class="sxs-lookup"><span data-stu-id="d41f5-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d41f5-102">Détails</span><span class="sxs-lookup"><span data-stu-id="d41f5-102">Details</span></span>|<span data-ttu-id="d41f5-103">À compter de .NET Framework 4.5.2, les projets VB.NET ne peuvent plus spécifier d’API System.Windows avec des espaces de noms partiellement qualifiés.</span><span class="sxs-lookup"><span data-stu-id="d41f5-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="d41f5-104">Par exemple, la référence à <code>Windows.Forms.DialogResult</code> échoue.</span><span class="sxs-lookup"><span data-stu-id="d41f5-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="d41f5-105">Le code doit référencer le nom qualifié complet (<xref:System.Windows.Forms.DialogResult>) ou importer l’espace de noms et référencer <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="d41f5-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="d41f5-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="d41f5-106">Suggestion</span></span>|<span data-ttu-id="d41f5-107">Le code doit être mis à jour pour référencer les API <code>System.Windows</code> avec des noms simples (en important l’espace de noms nécessaire) ou avec des noms qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="d41f5-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="d41f5-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="d41f5-108">Scope</span></span>|<span data-ttu-id="d41f5-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="d41f5-109">Minor</span></span>|
|<span data-ttu-id="d41f5-110">Version</span><span class="sxs-lookup"><span data-stu-id="d41f5-110">Version</span></span>|<span data-ttu-id="d41f5-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d41f5-111">4.5.2</span></span>|
|<span data-ttu-id="d41f5-112">Type</span><span class="sxs-lookup"><span data-stu-id="d41f5-112">Type</span></span>|<span data-ttu-id="d41f5-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="d41f5-113">Retargeting</span></span>|
