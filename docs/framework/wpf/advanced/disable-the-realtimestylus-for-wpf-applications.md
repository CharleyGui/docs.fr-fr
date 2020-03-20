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
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Désactiver RealTimeStylus pour les applications WPF

Windows Presentation Foundation (WPF) a construit à l’appui pour le traitement de Windows 7 entrée tactile. Le support vient à travers l’entrée de stylet <xref:System.Windows.UIElement.OnStylusUp%2A>en <xref:System.Windows.UIElement.OnStylusMove%2A> temps réel de la plate-forme tablette comme <xref:System.Windows.UIElement.OnStylusDown%2A>, , et les événements. Windows 7 fournit également des entrées multi-touch sous forme de messages de fenêtre Win32 WM_TOUCH. Ces deux API s’excluent mutuellement sur le même HWND. L’activation de l’entrée tactile via la plate-forme de tablette (par défaut pour les applications WPF) désactive WM_TOUCH messages. Par conséquent, pour utiliser WM_TOUCH pour recevoir des messages tactiles d’une fenêtre WPF, vous devez désactiver le support de stylet intégré dans WPF. Ceci est applicable dans un scénario tel qu’une fenêtre WPF hébergeant un composant qui utilise WM_TOUCH.  
  
 Pour désactiver WPF à l’écoute de l’entrée de stylet, supprimez tout support de tablette ajouté par la fenêtre WPF.  
  
## <a name="example"></a> Exemple  
 Le code d’échantillon suivant montre comment supprimer le support de la plate-forme de tablette par défaut en utilisant la réflexion.  
  
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
