---
title: Désactiver RealTimeStylus pour les applications WPF
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: acae177e1c49a6a1161bcf48f8e2e8ac1bfe13b8
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991837"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>Désactiver RealTimeStylus pour les applications WPF
Windows Presentation Foundation (WPF) dispose d’une prise en charge intégrée pour le traitement des entrées tactiles Windows 7. La prise en charge s’effectue par le biais de l’entrée de stylet <xref:System.Windows.UIElement.OnStylusDown%2A>en <xref:System.Windows.UIElement.OnStylusUp%2A>temps réel <xref:System.Windows.UIElement.OnStylusMove%2A> de la plateforme Tablet, sous la forme d’événements, et. Windows 7 fournit également des entrées tactiles multiples sous forme de messages de fenêtre Win32 WM_TOUCH. Ces deux API s’excluent mutuellement sur le même HWND. L’activation de l’entrée tactile via la plateforme de tablette (la valeur par défaut pour les applications WPF) désactive les messages WM_TOUCH. Par conséquent, pour utiliser WM_TOUCH pour recevoir des messages tactiles à partir d’une fenêtre WPF, vous devez désactiver la prise en charge intégrée du stylet dans WPF. Cela s’applique dans un scénario tel qu’une fenêtre WPF hébergeant un composant qui utilise WM_TOUCH.  
  
 Pour désactiver l’écoute WPF de l’entrée de stylet, supprimez toute prise en charge de tablette ajoutée par la fenêtre WPF.  
  
## <a name="example"></a>Exemples  
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
