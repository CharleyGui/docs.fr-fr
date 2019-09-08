---
title: Applications clientes sécurisées
ms.date: 03/30/2017
ms.assetid: 6239592e-fa7d-4dea-9f00-d296d0048b01
ms.openlocfilehash: 15d2b2199344644392be0e9a530c046a77db8523
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794383"
---
# <a name="secure-client-applications"></a>Applications clientes sécurisées
Les applications se composent généralement de nombreuses parties qui doivent toutes être protégées face aux vulnérabilités susceptibles d'entraîner une perte de données ou compromettre d'une autre manière le système. La création d'interfaces utilisateur sécurisées peut empêcher de nombreux problèmes en bloquant les attaquants avant qu'ils puissent accéder aux données ou aux ressources système.  
  
## <a name="validate-user-input"></a>Valider les entrées d'utilisateur  
 Lors de la construction d'une application qui accède à des données, vous devez vous baser sur l'hypothèse que toute entrée d'utilisateur est malveillante jusqu'à preuve du contraire. Si vous ne le faites pas, votre application sera vulnérable aux attaques. Le .NET Framework contient des classes pour vous aider à appliquer un domaine de valeurs pour les contrôles d'entrées, comme la limitation du nombre de caractères qui peuvent être entrés. Les connexions d'événement vous permettent d'écrire des procédures pour contrôler la validité des valeurs. Les données d'entrée d'utilisateur peuvent être validées et fortement typées, ce qui limite l'exposition d'une application aux attaques de script et par injection de code SQL.  
  
> [!IMPORTANT]
> Vous devez également valider l'entrée d'utilisateur au niveau de la source de données, ainsi que dans l'application cliente. Un attaquant peut choisir de contourner votre application et d'attaquer la source de données directement.  
  
 [Sécurité et entrées d’utilisateur](../../../standard/security/security-and-user-input.md)  
 Explique comment gérer des bogues subtils et potentiellement dangereux qui impliquent une entrée d'utilisateur.  
  
 [Validation de l’entrée d’utilisateur dans pages Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/7kh55542(v=vs.100))  
 Vue d’ensemble de la validation d’une entrée d’utilisateur à l’aide des contrôles de validation ASP.NET.  
  
 [Entrées d’utilisateur dans les Windows Forms](../../winforms/user-input-in-windows-forms.md)  
 Fournit des liens et des informations relatifs à la validation des entrées de la souris et au clavier dans une application Windows Forms.  
  
 [.NET Framework (expressions régulières)](../../../standard/base-types/regular-expressions.md)  
 Explique comment utiliser la classe <xref:System.Text.RegularExpressions.Regex> pour vérifier la validité des entrées d'utilisateur.  
  
## <a name="windows-applications"></a>Applications Windows  
 Auparavant, les applications Windows s'exécutaient généralement avec toutes les autorisations. Le .NET Framework fournit l'infrastructure permettant de restreindre l'exécution du code dans une application Windows en utilisant la sécurité d'accès du code. Toutefois, la sécurité d'accès du code seule n'est pas suffisante pour protéger votre application.  
  
 [Sécurité de Windows Forms](../../winforms/windows-forms-security.md)  
 Explique comment sécuriser des applications Windows Forms et fournit des liens vers des rubriques connexes.  
  
 [Applications Windows Forms et non managées](../../winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 Explique comment interagir avec des applications non managées dans une application Windows Forms.  
  
 [Déploiement ClickOnce pour les Windows Forms](../../winforms/clickonce-deployment-for-windows-forms.md)  
 Explique comment utiliser un déploiement `ClickOnce` dans une application Windows Forms et traite des implications en matière de sécurité.  
  
## <a name="aspnet-and-xml-web-services"></a>ASP.NET et services web XML  
 Les applications ASP.NET doivent généralement restreindre l’accès à certaines portions du site web et fournissent d’autres mécanismes de protection des données et de sécurité du site. Ces liens fournissent des informations utiles pour sécuriser votre application ASP.NET.  
  
 Un service web XML fournit des données qui peuvent être consommées par une application ASP.NET, une application Windows Forms ou un autre service web. Vous devez gérer la sécurité pour le service Web lui-même, ainsi que la sécurité pour l'application cliente.  
  
 Pour plus d'informations, voir les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Sécurisation des sites Web ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))|Explique comment sécuriser des applications ASP.NET.|  
|[Sécurisation des services Web XML créés à l’aide de ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))|Explique comment implémenter la sécurité pour un service Web ASP.NET.|  
|[Vue d’ensemble des attaques de script](https://docs.microsoft.com/previous-versions/aspnet/w1sw53ds(v=vs.100))|Explique comment se protéger d’une attaque de script, qui tente d’insérer des caractères nuisibles dans une page web.|  
|[Pratiques de sécurité de base pour les applications Web](https://docs.microsoft.com/previous-versions/aspnet/zdh19h94(v=vs.100))|Informations générales sur la sécurité et liens vers une présentation additionnelle.|  
  
## <a name="remoting"></a>Communication à distance  
 .NET Remoting vous permet de créer aisément des applications largement distribuées, que les composants d'application se trouvent tous sur un même ordinateur ou soient dispersés dans le monde entier. Vous pouvez générer des applications clientes qui utilisent des objets dans d'autres processus sur le même ordinateur ou sur tout autre ordinateur qui est accessible sur son réseau. Vous pouvez également utiliser .NET Remoting pour communiquer avec d'autres domaines d'application dans le même processus.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Configuration des applications distantes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b8tysty8(v=vs.100))|Explique comment configurer les applications de communication à distance pour éviter les problèmes courants.|  
|[Sécurité dans la communication à distance](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9hwst9th(v=vs.100))|Décrit l'authentification et le chiffrement, ainsi que des rubriques de sécurité supplémentaires relatives à la communication à distance.|  
|[Considérations relatives à la sécurité et à la communication à distance](../../misc/security-and-remoting-considerations.md)|Décrit les problèmes de sécurité liés aux objets protégés et au franchissement de domaine d'application.|  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](securing-ado-net-applications.md)
- [Recommandations pour les stratégies d’accès aux données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/8fxztkff(v=vs.90))
- [Sécurisation des applications](/visualstudio/ide/securing-applications)
- [Protection des informations de connexion](protecting-connection-information.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
