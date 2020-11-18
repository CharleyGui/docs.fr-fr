---
title: Emprunt et restauration d'identité
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
ms.openlocfilehash: 90f43510eb0e71fb324012fa00ac08f9ee3292ac
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820057"
---
# <a name="impersonating-and-reverting"></a>Emprunt et restauration d'identité

> [!NOTE]
> Cet article s’applique à Windows.
>
> Pour plus d’informations sur la ASP.NET Core, consultez [ASP.net Core Security](/aspnet/core/security/).

Parfois, vous devez obtenir un jeton de compte Windows pour emprunter l’identité d’un compte Windows. Par exemple, votre application ASP.NET peut devoir agir pour le compte de plusieurs utilisateurs à des moments différents. Votre application peut accepter un jeton représentant un administrateur à partir d’Internet Information Services (IIS), emprunter l’identité de cet utilisateur, effectuer une opération et revenir à l’identité précédente. Ensuite, elle peut accepter un jeton d’IIS représentant un utilisateur disposant de droits inférieurs, effectuer une opération et revenir à nouveau à l’identité précédente.  
  
 Dans les situations où votre application doit emprunter l’identité d’un compte Windows qui n’a pas été attaché au thread actuel par IIS, vous devez extraire le jeton du compte et l’utiliser pour activer le compte. Pour cela, procédez comme suit :  
  
1. Récupérez le jeton de compte pour un utilisateur particulier en appelant la méthode **LogonUser** non managée. Cette méthode n’est pas dans la bibliothèque de classes de base .NET, mais elle se trouve dans le **advapi32.dll** non managé. L’accès aux méthodes dans du code non managé est une opération complexe qui dépasse le cadre de cette discussion. Pour plus d’informations, consultez [Interopération avec du code non managé](../../framework/interop/index.md). Pour plus d’informations sur la méthode **LogonUser** et **advapi32.dll**, consultez la documentation du SDK de la plateforme.  
  
2. Créez une nouvelle instance de la classe **WindowsIdentity**, qui passe le jeton. Le code suivant illustre cet appel, où `hToken` désigne un jeton Windows.  
  
    ```csharp  
    WindowsIdentity impersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim impersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3. Commencez l’emprunt d’identité en créant une instance de la classe <xref:System.Security.Principal.WindowsImpersonationContext> et en l’initialisant avec la méthode <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType> de la classe initialisée, comme illustré dans le code suivant.  
  
    ```csharp  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext myImpersonation = impersonatedIdentity.Impersonate()  
    ```  
  
4. Quand vous n’avez plus besoin d’emprunter l’identité, appelez la méthode <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType> pour rétablir l’emprunt d’identité, comme illustré dans le code suivant.  
  
    ```csharp  
    myImpersonation.Undo();  
    ```  
  
    ```vb  
    myImpersonation.Undo()  
    ```  
  
 Si du code approuvé a déjà attaché un <xref:System.Security.Principal.WindowsPrincipal> objet au thread, vous pouvez appeler la méthode d’instance **Impersonate**, qui ne prend pas de jeton de compte. Notez que cela est utile uniquement lorsque l’objet **WindowsPrincipal** sur le thread représente un utilisateur autre que celui sous lequel le processus est exécuté. Par exemple, vous pouvez rencontrer cette situation quand vous utilisez ASP.NET avec l’authentification Windows activée et l’emprunt d’identité désactivé. Dans ce cas, le processus s’exécute sous un compte configuré dans Internet Information Services (IIS), tandis que le principal actuel représente l’utilisateur Windows qui accède à la page.  
  
 Notez que ni **Impersonate** ni **Undo** ne modifie l’objet **principal** ( <xref:System.Security.Principal.IPrincipal> ) associé au contexte d’appel actuel. Au lieu de cela, l’emprunt d’identité et le rétablissement modifient le jeton associé au processus du système d’exploitation actuel.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Principal.WindowsIdentity>
- <xref:System.Security.Principal.WindowsImpersonationContext>
- [Objets Principal et Identity](principal-and-identity-objects.md)
- [Interopération avec du code non managé](../../framework/interop/index.md)
- [Sécurité ASP.NET Core](/aspnet/core/security/)
