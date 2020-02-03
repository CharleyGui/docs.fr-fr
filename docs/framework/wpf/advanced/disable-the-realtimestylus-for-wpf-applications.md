---
title: Désactiver l’RealTimeStylus
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: 74145c32af7e9ebbc774a0301e205aa1eb1539b3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737942"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a><span data-ttu-id="4f2e0-102">Désactiver RealTimeStylus pour les applications WPF</span><span class="sxs-lookup"><span data-stu-id="4f2e0-102">Disable the RealTimeStylus for WPF Applications</span></span>

<span data-ttu-id="4f2e0-103">Windows Presentation Foundation (WPF) dispose d’une prise en charge intégrée pour le traitement des entrées tactiles Windows 7.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-103">Windows Presentation Foundation (WPF) has built in support for processing Windows 7 touch input.</span></span> <span data-ttu-id="4f2e0-104">La prise en charge s’effectue par le biais de l’entrée de stylet en temps réel de la plateforme Tablet, sous la forme d’événements <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>et <xref:System.Windows.UIElement.OnStylusMove%2A>.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-104">The support comes through the tablet platform’s real-time stylus input as <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>, and <xref:System.Windows.UIElement.OnStylusMove%2A> events.</span></span> <span data-ttu-id="4f2e0-105">Windows 7 fournit également une entrée tactile multipoint comme des messages de fenêtre Win32 WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-105">Windows 7 also provides multi-touch input as Win32 WM_TOUCH window messages.</span></span> <span data-ttu-id="4f2e0-106">Ces deux API s’excluent mutuellement sur le même HWND.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-106">These two APIs are mutually exclusive on the same HWND.</span></span> <span data-ttu-id="4f2e0-107">L’activation de l’entrée tactile via la plateforme de tablette (la valeur par défaut pour les applications WPF) désactive les messages de WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-107">Enabling touch input via the tablet platform (the default for WPF applications) disables WM_TOUCH messages.</span></span> <span data-ttu-id="4f2e0-108">Par conséquent, pour utiliser WM_TOUCH pour recevoir des messages tactiles à partir d’une fenêtre WPF, vous devez désactiver la prise en charge intégrée du stylet dans WPF.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-108">As a result, to use WM_TOUCH to receive touch messages from a WPF window, you must disable the built-in stylus support in WPF.</span></span> <span data-ttu-id="4f2e0-109">Cela s’applique dans un scénario tel qu’une fenêtre WPF hébergeant un composant qui utilise WM_TOUCH.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-109">This is applicable in a scenario such as a WPF window hosting a component that uses WM_TOUCH.</span></span>  
  
 <span data-ttu-id="4f2e0-110">Pour désactiver l’écoute WPF de l’entrée de stylet, supprimez toute prise en charge de tablette ajoutée par la fenêtre WPF.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-110">To disable WPF listening to stylus input, remove any tablet support added by the WPF window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f2e0-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="4f2e0-111">Example</span></span>  
 <span data-ttu-id="4f2e0-112">L’exemple de code suivant montre comment supprimer la prise en charge par défaut de la plateforme Tablet à l’aide de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="4f2e0-112">The following sample code shows how to remove the default tablet platform support by using reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f2e0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f2e0-113">See also</span></span>

- [<span data-ttu-id="4f2e0-114">Interception d'entrée à partir du stylet</span><span class="sxs-lookup"><span data-stu-id="4f2e0-114">Intercepting Input from the Stylus</span></span>](intercepting-input-from-the-stylus.md)
