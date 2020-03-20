---
title: Désactiver le RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: c2500b494f76c85e4b23823a44a180d85d5092ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186081"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="56c49-102">Désactiver RealTimeStylus pour les applications WPF</span><span class="sxs-lookup"><span data-stu-id="56c49-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="56c49-103">Windows Presentation Foundation (WPF) a construit à l’appui pour le traitement de Windows 7 entrée tactile.</span><span class="sxs-lookup"><span data-stu-id="56c49-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="56c49-104">Le support vient à travers l’entrée de stylet <xref:System.Windows.UIElement.OnStylusUp%2A>en <xref:System.Windows.UIElement.OnStylusMove%2A> temps réel de la plate-forme tablette comme <xref:System.Windows.UIElement.OnStylusDown%2A>, , et les événements.</span><span class="sxs-lookup"><span data-stu-id="56c49-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="56c49-105">Windows 7 fournit également des entrées multi-touch sous forme de messages de fenêtre Win32 WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="56c49-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="56c49-106">Ces deux API s’excluent mutuellement sur le même HWND.</span><span class="sxs-lookup"><span data-stu-id="56c49-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="56c49-107">L’activation de l’entrée tactile via la plate-forme de tablette (par défaut pour les applications WPF) désactive WM_TOUCH messages.</span><span class="sxs-lookup"><span data-stu-id="56c49-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="56c49-108">Par conséquent, pour utiliser WM_TOUCH pour recevoir des messages tactiles d’une fenêtre WPF, vous devez désactiver le support de stylet intégré dans WPF.</span><span class="sxs-lookup"><span data-stu-id="56c49-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="56c49-109">Ceci est applicable dans un scénario tel qu’une fenêtre WPF hébergeant un composant qui utilise WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="56c49-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="56c49-110">Pour désactiver WPF à l’écoute de l’entrée de stylet, supprimez tout support de tablette ajouté par la fenêtre WPF.</span><span class="sxs-lookup"><span data-stu-id="56c49-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56c49-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="56c49-111">Example</span></span>  
 <span data-ttu-id="56c49-112">Le code d’échantillon suivant montre comment supprimer le support de la plate-forme de tablette par défaut en utilisant la réflexion.</span><span class="sxs-lookup"><span data-stu-id="56c49-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
```csharp  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="56c49-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56c49-113">See also</span></span>

- [<span data-ttu-id="56c49-114">Interception d'entrée à partir du stylet</span><span class="sxs-lookup"><span data-stu-id="56c49-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
