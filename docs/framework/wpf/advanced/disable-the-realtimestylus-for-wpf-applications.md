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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Désactiver RealTimeStylus pour les applications WPF

Windows Presentation Foundation (WPF) dispose d’une prise en charge intégrée pour le traitement des entrées tactiles Windows 7. La prise en charge s’effectue par le biais de l’entrée de stylet en temps réel de la plateforme Tablet, sous la forme d’événements <xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusUp%2A>et <xref:System.Windows.UIElement.OnStylusMove%2A>. Windows 7 fournit également une entrée tactile multipoint comme des messages de fenêtre Win32 WM_TOUCH. Ces deux API s’excluent mutuellement sur le même HWND. L’activation de l’entrée tactile via la plateforme de tablette (la valeur par défaut pour les applications WPF) désactive les messages de WM_TOUCH. Par conséquent, pour utiliser WM_TOUCH pour recevoir des messages tactiles à partir d’une fenêtre WPF, vous devez désactiver la prise en charge intégrée du stylet dans WPF. Cela s’applique dans un scénario tel qu’une fenêtre WPF hébergeant un composant qui utilise WM_TOUCH.  
  
 Pour désactiver l’écoute WPF de l’entrée de stylet, supprimez toute prise en charge de tablette ajoutée par la fenêtre WPF.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment supprimer la prise en charge par défaut de la plateforme Tablet à l’aide de la réflexion.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Interception d'entrée à partir du stylet](intercepting-input-from-the-stylus.md)
