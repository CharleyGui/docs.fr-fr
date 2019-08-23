---
title: Considérations sur l'hébergement d'un contrôle ActiveX dans un Windows Form
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 0b95bab20299b966b9f3c6e6ce089a641670f974
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933416"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Considérations sur l'hébergement d'un contrôle ActiveX dans un Windows Form
Bien que les Windows Forms aient été optimisés pour héberger des contrôles Windows Forms, vous pouvez néanmoins utiliser des contrôles ActiveX. Gardez à l’esprit les considérations suivantes lors de la planification d’une application qui utilise des contrôles ActiveX :  
  
- **Sécurité** : le common language runtime a été amélioré en ce qui concerne la sécurité d’accès du code. Les applications recourant aux Windows Forms peuvent fonctionner sans problème dans un environnement totalement fiable et dans un environnement partiellement fiable avec la plupart des fonctionnalités disponibles. Les contrôles Windows Forms peuvent être hébergés dans un navigateur sans aucune complication. Cependant, les contrôles ActiveX dans les Windows Forms ne tirent pas parti de ces améliorations de sécurité. L’exécution d’un contrôle ActiveX nécessite une autorisation de code non managé, qui est <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> définie avec la propriété. Pour plus d’informations sur la sécurité et l’autorisation de code non <xref:System.Security.Permissions.SecurityPermissionAttribute>managé, consultez.  
  
- **Coût total de possession** : les contrôles ActiveX ajoutés à un Windows Form sont déployés dans leur intégralité avec ce Windows Form, ce qui peut accroître considérablement la taille des fichiers créés. En outre, l’utilisation de contrôles ActiveX sur des Windows Forms nécessite l’écriture dans le Registre. Ceci est plus invasif sur l’ordinateur d’un utilisateur que les contrôles Windows Forms, qui ne le nécessitent pas.  
  
    > [!NOTE]
    > L’utilisation d’un contrôle ActiveX nécessite l’utilisation d’un wrapper COM interop. Pour plus d’informations, consultez [Interopérabilité COM en Visual Basic et Visual C#](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    > Si le nom d’un membre du contrôle ActiveX correspond à un nom défini dans le .NET Framework, l’importateur de contrôles ActiveX fait précéder le nom du membre de la liste de <xref:System.Windows.Forms.AxHost> certificats de **confiance** lorsqu’il crée la classe dérivée. Par exemple, si votre contrôle ActiveX possède un membre nommé **Layout**, il est renommé **CtlLayout** dans la classe dérivée de AxHost, car l’événement **Layout** est défini dans le .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique : Ajouter des contrôles ActiveX à Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Sécurité d’accès du code](../../misc/code-access-security.md)
- [Comparaison des contrôles et des objets programmables dans divers langages et bibliothèques](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Placement de contrôles dans les Windows Forms](putting-controls-on-windows-forms.md)
- [Contrôles Windows Forms](index.md)
