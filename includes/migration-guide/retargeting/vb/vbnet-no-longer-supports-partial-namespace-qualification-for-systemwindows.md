---
ms.openlocfilehash: 43e9c1c2f03daedf4d56152da5672b89399a3c69
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804669"
---
### <a name="vbnet-no-longer-supports-partial-namespace-qualification-for-systemwindows-apis"></a><span data-ttu-id="96963-101">VB.NET ne prend plus en charge la qualification partielle des espaces de noms pour les API System.Windows</span><span class="sxs-lookup"><span data-stu-id="96963-101">VB.NET no longer supports partial namespace qualification for System.Windows APIs</span></span>

|   |   |
|---|---|
|<span data-ttu-id="96963-102">Détails</span><span class="sxs-lookup"><span data-stu-id="96963-102">Details</span></span>|<span data-ttu-id="96963-103">À compter de .NET Framework 4.5.2, les projets VB.NET ne peuvent plus spécifier d’API System.Windows avec des espaces de noms partiellement qualifiés.</span><span class="sxs-lookup"><span data-stu-id="96963-103">Beginning in .NET Framework 4.5.2, VB.NET projects cannot specify System.Windows APIs with partially-qualified namespaces.</span></span> <span data-ttu-id="96963-104">Par exemple, la référence à <code>Windows.Forms.DialogResult</code> échoue.</span><span class="sxs-lookup"><span data-stu-id="96963-104">For example, referring to <code>Windows.Forms.DialogResult</code> will fail.</span></span> <span data-ttu-id="96963-105">Le code doit référencer le nom qualifié complet (<xref:System.Windows.Forms.DialogResult>) ou importer l’espace de noms et référencer <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span><span class="sxs-lookup"><span data-stu-id="96963-105">Instead, code must refer to the fully qualified name (<xref:System.Windows.Forms.DialogResult>) or import the specific namespace and refer simply to <xref:System.Windows.Forms.DialogResult?displayProperty=name>.</span></span>|
|<span data-ttu-id="96963-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="96963-106">Suggestion</span></span>|<span data-ttu-id="96963-107">Le code doit être mis à jour pour référencer les API <code>System.Windows</code> avec des noms simples (en important l’espace de noms nécessaire) ou avec des noms qualifiés complets.</span><span class="sxs-lookup"><span data-stu-id="96963-107">Code should be updated to refer to <code>System.Windows</code> APIs either with simple names (and importing the relevant namespace) or with fully qualified names.</span></span>|
|<span data-ttu-id="96963-108">Portée</span><span class="sxs-lookup"><span data-stu-id="96963-108">Scope</span></span>|<span data-ttu-id="96963-109">Mineur</span><span class="sxs-lookup"><span data-stu-id="96963-109">Minor</span></span>|
|<span data-ttu-id="96963-110">Version</span><span class="sxs-lookup"><span data-stu-id="96963-110">Version</span></span>|<span data-ttu-id="96963-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="96963-111">4.5.2</span></span>|
|<span data-ttu-id="96963-112">Type</span><span class="sxs-lookup"><span data-stu-id="96963-112">Type</span></span>|<span data-ttu-id="96963-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="96963-113">Retargeting</span></span>|

