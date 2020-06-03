---
title: 'Atténuation : cadres PNG dans les objets Icon'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
ms.openlocfilehash: 713e6a0fa615ac748134fac501e5142a65e434f1
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248893"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="bfcc7-102">Atténuation : cadres PNG dans les objets Icon</span><span class="sxs-lookup"><span data-stu-id="bfcc7-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="bfcc7-103">À compter du .NET Framework 4.6, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> convertit correctement les icônes dotées de cadres PNG en objets <xref:System.Drawing.Bitmap> .</span><span class="sxs-lookup"><span data-stu-id="bfcc7-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="bfcc7-104">Dans les applications qui ciblent le .NET Framework 4.5.2 et les versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet <xref:System.Drawing.Icon> comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="bfcc7-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="bfcc7-105">Impact</span><span class="sxs-lookup"><span data-stu-id="bfcc7-105">Impact</span></span>  
 <span data-ttu-id="bfcc7-106">Cette modification affecte les applications qui sont recompilées pour cibler le .NET Framework 4.6 et qui implémentent un traitement spécial pour l’exception <xref:System.ArgumentOutOfRangeException> qui est levée quand un objet <xref:System.Drawing.Icon> comporte des cadres PNG.</span><span class="sxs-lookup"><span data-stu-id="bfcc7-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="bfcc7-107">Dans le cadre d’une exécution sous le .NET Framework 4.6, la conversion aboutit, il n’est plus levé d’exception <xref:System.ArgumentOutOfRangeException> et, de ce fait, le gestionnaire d’exceptions n’est plus appelé.</span><span class="sxs-lookup"><span data-stu-id="bfcc7-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="bfcc7-108">Limitation des risques</span><span class="sxs-lookup"><span data-stu-id="bfcc7-108">Mitigation</span></span>  
 <span data-ttu-id="bfcc7-109">Si ce comportement n’est pas souhaitable, vous pouvez conserver le comportement précédent en ajoutant l’élément suivant à la section [ \< > du runtime](../configure-apps/file-schema/runtime/runtime-element.md) de votre fichier app. config :</span><span class="sxs-lookup"><span data-stu-id="bfcc7-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="bfcc7-110">Si le fichier app.config contient déjà l’élément `AppContextSwitchOverrides` , la nouvelle valeur doit être fusionnée avec l’attribut `value` comme ceci :</span><span class="sxs-lookup"><span data-stu-id="bfcc7-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;previous key=previous-value" />
```
  
## <a name="see-also"></a><span data-ttu-id="bfcc7-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfcc7-111">See also</span></span>

- [<span data-ttu-id="bfcc7-112">Compatibilité des applications</span><span class="sxs-lookup"><span data-stu-id="bfcc7-112">Application compatibility</span></span>](application-compatibility.md)
