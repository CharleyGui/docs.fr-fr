---
title: Demandes de liaison
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
ms.openlocfilehash: a0466eb5c24840c77a3b191f9b0e001f6b267fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181170"
---
# <a name="link-demands"></a>Demandes de liaison
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Une demande de liaison entraîne une vérification de sécurité pendant la compilation juste-à-temps. Seul l'assembly appelant immédiat de votre code est vérifié. La liaison est établie quand le code est lié à une référence de type, y compris les références de pointeur fonction et les appels de méthode. Si l'assembly appelant ne dispose pas des autorisations suffisantes pour établir une liaison avec votre code, la liaison n'est pas autorisée et une exception d'exécution est levée quand le code est chargé et exécuté. Les demandes de liaison peuvent être substituées dans les classes qui héritent de votre code.  
  
 Notez qu'un parcours de pile complet n'est pas exécuté avec ce type de demande et que votre code est toujours susceptible de subir des attaques malveillantes. Par exemple, si une méthode d’assemblage A est protégée par une demande de lien, un appelant direct dans l’assemblage B est évalué en fonction des autorisations de l’Assemblée B.  Toutefois, la demande de lien n’évaluera pas une méthode dans l’assemblage C si elle appelle indirectement la méthode dans l’assemblage A en utilisant la méthode dans l’assemblage B. La demande de lien spécifie que les autorisations des appelants directs dans l’assemblage d’appels immédiats doivent avoir à lier à votre code. Elle ne spécifie pas les autorisations que tous les appelants doivent avoir pour exécuter votre code.  
  
 Les modificateurs de parcours de pile <xref:System.Security.CodeAccessPermission.Assert%2A>, <xref:System.Security.CodeAccessPermission.Deny%2A> et <xref:System.Security.CodeAccessPermission.PermitOnly%2A> n'affectent pas l'évaluation des demandes de liaison.  Étant donné que les demandes de liaison n'effectuent pas de parcours de pile, les modificateurs de parcours de pile n'ont aucun effet sur les demandes de liaison.  
  
 Si une méthode protégée par une demande de lien est accessible par [La réflexion,](../reflection-and-codedom/reflection.md)alors une demande de lien vérifie l’appelant immédiat du code consulté par la réflexion. Cela est vrai à la fois pour les détections de méthodes et les appels de méthodes effectués à l'aide de la réflexion. Par exemple, supposons que <xref:System.Reflection.MethodInfo> le code utilise la réflexion pour renvoyer un objet représentant une méthode protégée par une demande de lien, puis passe cet objet **MethodInfo** à un autre code qui utilise l’objet pour invoquer la méthode originale. Dans ce cas, le contrôle de la demande de lien se produit deux fois: une fois pour le code qui renvoie **l’objet MethodInfo** et une fois pour le code qui l’invoque.  
  
> [!NOTE]
> Une demande de liaison exécutée sur un constructeur de classe statique ne protège pas le constructeur, car les constructeurs statiques sont appelés par le système, en dehors du chemin d’exécution du code de l’application. Par conséquent, quand une demande de liaison est appliquée à une classe entière, elle ne peut pas protéger l'accès à un constructeur statique, même si elle protège le reste de la classe.  
  
 Le fragment de code suivant spécifie de manière déclarative que tout code lié à la méthode `ReadData` doit avoir l'autorisation `CustomPermission`. Cette autorisation est une autorisation personnalisée hypothétique et n'existe pas dans le .NET Framework. La demande est faite en passant un drapeau **SecurityAction.LinkDemand** à la `CustomPermissionAttribute`.  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Attributs](../../standard/attributes/index.md)
- [Sécurité d’accès au code](code-access-security.md)
