---
title: Création de ma première application web ASP.NET prenant en charge les revendications
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: db5060826d3bfcc259c098a160354892a050554c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422394"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Création de ma première application web ASP.NET prenant en charge les revendications
## <a name="applies-to"></a>S'applique à  
  
- Windows Identity Foundation (WIF)  
  
- ASP.NET  
  
 Cette rubrique décrit le scénario de création des applications Web qui prennent en charge les revendications ASP.NET à l'aide de WIF. Il y a généralement trois participants dans un scénario d'application qui prend en charge les revendications : l'application elle-même, l'utilisateur final et le service d'émission de jeton de sécurité (STS). L'illustration suivante décrit ce scénario :  
  
 ![Diagramme montrant un composants WIF base Web App.](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. L'application prenant en charge les revendications utilise WIF pour identifier des demandes non authentifiées et pour les rediriger vers STS.  
  
2. L'utilisateur final fournit les informations d'identification à STS et une fois qu'il est authentifié, un jeton est émis par STS pour l'utilisateur.  
  
3. L'utilisateur est redirigé à partir de STS vers l'application prenant en charge les revendications avec le jeton publié par STS dans la demande.  
  
4. L'application qui prend en charge les revendications est configurée pour approuver STS et les jetons qu'il émet. L'application qui prend en charge les revendications utilise WIF pour valider le jeton et l'analyser. Les développeurs utilisent l’API WIF et les types appropriés, par exemple **ClaimsPrincipal**, pour les besoins de l’application, tels que l’implémentation de l’autorisation pour cette dernière.  
  
 À partir de la version .NET 4.5, WIF fait partie du package .NET Framework. Le fait d’avoir les classes WIF directement disponibles dans l’infrastructure permet une intégration plus profonde de l’identité basée sur les revendications dans .NET, facilitant ainsi l’utilisation des revendications. Avec WIF 4.5, vous n'avez pas besoin d'installer de composant hors plage pour démarrer le développement d'applications Web qui prennent en charge les revendications. Les classes WIF sont maintenant réparties sur plusieurs assemblys, les principaux étant System.Security.Claims, System.IdentityModel et System.IdentityModel.Services.  
  
 STS est un service qui émet des jetons en cas de réussite de l'authentification. Microsoft propose deux STS standard compatibles :  
  
- [Active Directory Federation Services (ADFS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 AD FS 2.0 fait partie de Windows Server R2 et peut être utilisé comme un STS pour les scénarios sur site. ACS est un service Cloud, proposé dans le cadre de la plateforme Microsoft Azure. À des fins de test ou à titre éducatif, vous pouvez également utiliser d'autres STS pour générer des applications qui prennent en charge les revendications. Par exemple, vous pouvez utiliser le développement STS Local qui fait partie de la [Identity and Access Tool pour Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) qui est disponible gratuitement en ligne.  
  
 Pour créer votre première application ASP.NET. NET prenant en charge les revendications à l'aide de WIF, suivez les instructions de l'une des opérations suivantes :  
  
- [Guide pratique pour Création d’Application de Web prenant en charge les revendications ASP.NET MVC à l’aide de WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
- [Guide pratique pour Générer des revendications Application Web Forms ASP.NET à l’aide de WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
- [Guide pratique pour Création d’Application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main de WIF](../../../docs/framework/security/getting-started-with-wif.md)
