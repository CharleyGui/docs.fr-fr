---
title: 'Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400119"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="b3165-102">Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées</span><span class="sxs-lookup"><span data-stu-id="b3165-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="b3165-103">Dans les applications Windows Forms qui ciblent des versions du .NET Framework à partir de .NET Framework 4.6.1, une implémentation personnalisée de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> peut en toute sécurité filtrer les messages quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée si l’implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="b3165-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="b3165-104">Effectue l’une des actions suivantes ou les deux :</span><span class="sxs-lookup"><span data-stu-id="b3165-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="b3165-105">Ajout d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3165-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="b3165-106">Suppression d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="b3165-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="b3165-107">.</span><span class="sxs-lookup"><span data-stu-id="b3165-107">method.</span></span>

- <span data-ttu-id="b3165-108">**Et** pompe des messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3165-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="b3165-109">Impact</span><span class="sxs-lookup"><span data-stu-id="b3165-109">Impact</span></span>

<span data-ttu-id="b3165-110">Ce changement affecte uniquement les applications Windows Forms qui ciblent .NET Framework 4.6.1 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="b3165-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="b3165-111">Pour les applications Windows Forms qui ciblent des versions antérieures du .NET Framework, de telles implémentations lèvent dans certains cas une exception <xref:System.IndexOutOfRangeException> quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée.</span><span class="sxs-lookup"><span data-stu-id="b3165-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="b3165-112">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="b3165-112">Mitigation</span></span>

<span data-ttu-id="b3165-113">Si cette modification n’est pas souhaitable, les applications qui ciblent le cadre .NET 4.6.1 ou [ \<](../configure-apps/file-schema/runtime/runtime-element.md) une version ultérieure peuvent s’en retirer en ajoutant le paramètre de configuration suivant à la section>de configuration de l’application :</span><span class="sxs-lookup"><span data-stu-id="b3165-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="b3165-114">En outre, les applications qui ciblent les versions précédentes du cadre .NET mais sont en cours d’exécution sous le cadre .NET 4.6.1 ou une version ultérieure peuvent opter pour ce comportement en ajoutant le paramètre de configuration suivant à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application:</span><span class="sxs-lookup"><span data-stu-id="b3165-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="b3165-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3165-115">See also</span></span>

- [<span data-ttu-id="b3165-116">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="b3165-116">Application compatibility</span></span>](application-compatibility.md)
