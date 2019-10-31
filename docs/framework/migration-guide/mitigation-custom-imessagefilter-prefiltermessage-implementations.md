---
title: 'Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5174c67e4204c2e20e5730ab7c092ccbb0aeda1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126260"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="50f31-102">Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées</span><span class="sxs-lookup"><span data-stu-id="50f31-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="50f31-103">Dans les applications Windows Forms qui ciblent des versions du .NET Framework à partir de .NET Framework 4.6.1, une implémentation personnalisée de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> peut en toute sécurité filtrer les messages quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée si l’implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="50f31-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="50f31-104">Effectue l’une des actions suivantes ou les deux :</span><span class="sxs-lookup"><span data-stu-id="50f31-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="50f31-105">Ajout d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="50f31-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="50f31-106">Suppression d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="50f31-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="50f31-107">.</span><span class="sxs-lookup"><span data-stu-id="50f31-107">method.</span></span>

- <span data-ttu-id="50f31-108">**Et** pompe des messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="50f31-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="50f31-109">Impact</span><span class="sxs-lookup"><span data-stu-id="50f31-109">Impact</span></span>

<span data-ttu-id="50f31-110">Ce changement affecte uniquement les applications Windows Forms qui ciblent .NET Framework 4.6.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="50f31-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="50f31-111">Pour les applications Windows Forms qui ciblent des versions antérieures du .NET Framework, de telles implémentations lèvent dans certains cas une exception <xref:System.IndexOutOfRangeException> quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée.</span><span class="sxs-lookup"><span data-stu-id="50f31-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="50f31-112">Atténuation</span><span class="sxs-lookup"><span data-stu-id="50f31-112">Mitigation</span></span>

<span data-ttu-id="50f31-113">Si ce changement n’est pas souhaitable, les applications qui ciblent .NET Framework 4.6.1 ou versions ultérieures peuvent ne pas y adhérer en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="50f31-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="50f31-114">De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sous .NET Framework 4.6.1 ou versions ultérieures peuvent adhérer à ce comportement en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="50f31-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="50f31-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50f31-115">See also</span></span>

- [<span data-ttu-id="50f31-116">Modifications de reciblage</span><span class="sxs-lookup"><span data-stu-id="50f31-116">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
