---
title: 'Procédure : créer un objet WindowsPrincipal'
ms.date: 07/15/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET], creating a WindowsPrincipal object
- security [.NET], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
ms.openlocfilehash: 6cf7153250d2574783515ea53cf99709499d36f9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556204"
---
# <a name="how-to-create-a-windowsprincipal-object"></a>Procédure : créer un objet WindowsPrincipal

> [!NOTE]
> Cet article s’applique à Windows.
>
> Pour plus d’informations sur la ASP.NET Core, consultez [ASP.net Core Security](/aspnet/core/security/).

Il existe deux façons de créer un objet <xref:System.Security.Principal.WindowsPrincipal>, selon que le code doit effectuer une ou plusieurs validations basées sur les rôles.  
  
Si le code doit exécuter plusieurs validations basées sur les rôles, la première des procédures suivantes produira moins de surcharge. Si le code ne doit exécuter qu’une seule validation basée sur les rôles, vous pouvez créer un objet <xref:System.Security.Principal.WindowsPrincipal> à l’aide de la deuxième procédure ci-dessous.  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a>Pour créer un objet WindowsPrincipal pour une validation répétée  
  
1. Appelez la méthode <xref:System.AppDomain.SetPrincipalPolicy%2A> sur l'objet <xref:System.AppDomain> qui est retourné par la propriété statique <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType>, en passant à la méthode une valeur d'énumération <xref:System.Security.Principal.PrincipalPolicy> qui indique la nouvelle stratégie. Les valeurs prises en charge sont <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal> et <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>. Le code suivant illustre cet appel de méthode.  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2. Une fois la stratégie définie, utilisez la propriété statique <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> pour récupérer le principal qui encapsule l'utilisateur Windows actuel. Étant donné que le type de retour de la propriété est <xref:System.Security.Principal.IPrincipal>, vous devez caster le résultat vers un type <xref:System.Security.Principal.WindowsPrincipal>. Le code suivant initialise un nouvel objet <xref:System.Security.Principal.WindowsPrincipal> vers la valeur du principal associé au thread actuel.  
  
    ```csharp  
    WindowsPrincipal myPrincipal =
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim myPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)
    ```  
  
3. Quand l'objet principal a été créé, vous pouvez utiliser plusieurs méthodes pour le valider.  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a>Pour créer un objet WindowsPrincipal pour une validation unique  
  
1. Initialisez un nouvel objet <xref:System.Security.Principal.WindowsIdentity> en appelant la méthode statique <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType>, qui interroge le compte Windows actuel et place des informations sur ce compte dans l'objet d'identité récemment créé. Le code suivant crée un nouvel objet <xref:System.Security.Principal.WindowsIdentity> et l'initialise vers l'utilisateur authentifié actuel.  
  
    ```csharp  
    WindowsIdentity myIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim myIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2. Créez un objet <xref:System.Security.Principal.WindowsPrincipal> et passez-lui la valeur de l'objet <xref:System.Security.Principal.WindowsIdentity> créé à l'étape précédente.  
  
    ```csharp  
    WindowsPrincipal myPrincipal = new WindowsPrincipal(myIdentity);  
    ```  
  
    ```vb  
    Dim myPrincipal As New WindowsPrincipal(myIdentity)  
    ```  
  
3. Quand l'objet principal a été créé, vous pouvez utiliser plusieurs méthodes pour le valider.  
  
## <a name="see-also"></a>Voir aussi

- [Objets Principal et Identity](principal-and-identity-objects.md)
- [Sécurité ASP.NET Core](/aspnet/core/security/)
