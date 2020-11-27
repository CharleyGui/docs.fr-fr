---
title: 'Atténuation : cadres PNG dans les objets Icon'
description: Découvrez comment configurer le comportement des frames PNG dans les objets Icon si le nouveau comportement inclus dans .NET Framework 4,6 et versions ultérieures n’est pas souhaitable.
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: a8bb4fca19a09f16c89ce8c5da08ebcae9a037ec
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276579"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="0244f-103">Atténuation : cadres PNG dans les objets Icon</span><span class="sxs-lookup"><span data-stu-id="0244f-103">Mitigation: PNG Frames in Icon Objects</span></span>

<span data-ttu-id="0244f-104">À compter du .NET Framework 4.6, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> convertit correctement les icônes dotées de cadres PNG en objets <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="0244f-104">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="0244f-105">Dans les applications qui ciblent le .NET Framework 4.5.2 et les versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet <xref:System.Drawing.Icon> comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="0244f-105">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0244f-106">Impact</span><span class="sxs-lookup"><span data-stu-id="0244f-106">Impact</span></span>  

 <span data-ttu-id="0244f-107">Cette modification affecte les applications qui sont recompilées pour cibler le .NET Framework 4.6 et qui implémentent un traitement spécial pour l’exception <xref:System.ArgumentOutOfRangeException> qui est levée quand un objet <xref:System.Drawing.Icon> comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="0244f-107">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="0244f-108">Dans le cadre d’une exécution sous le .NET Framework 4.6, la conversion aboutit, il n’est plus levé d’exception <xref:System.ArgumentOutOfRangeException> et, de ce fait, le gestionnaire d’exceptions n’est plus appelé.</span><span class="sxs-lookup"><span data-stu-id="0244f-108">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="0244f-109">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="0244f-109">Mitigation</span></span>  

 <span data-ttu-id="0244f-110">Si ce comportement n’est pas souhaitable, vous pouvez conserver le comportement précédent en ajoutant l’élément suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="0244f-110">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="0244f-111">Si le fichier app.config contient déjà l’élément `AppContextSwitchOverrides` , la nouvelle valeur doit être fusionnée avec l’attribut `value` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="0244f-111">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="0244f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0244f-112">See also</span></span>

- [<span data-ttu-id="0244f-113">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="0244f-113">Application compatibility</span></span>](application-compatibility.md)
