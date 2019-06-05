---
title: Génération de mon premier service WCF prenant en charge les revendications
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: f242de43f1917dd6b01e15914359049ee754aa92
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690176"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Génération de mon premier service WCF prenant en charge les revendications
## <a name="applies-to"></a>S'applique à  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Vue d'ensemble  
 Cette rubrique décrit le scénario de création des services WCF qui prennent en charge les revendications à l'aide de WIF. Il y a généralement trois participants dans un scénario de service Web qui prend en charge les revendications : le service Web lui-même, l'utilisateur final, et le service d'émission de jeton de sécurité (STS). L'illustration suivante décrit ce scénario :  
  
 ![Diagramme montrant les composants WIF revendications prenant en charge Service WCF de base.](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. Le client du service WCF (parfois appelé agent) utilise WIF pour envoyer les informations d'identification à STS et une fois l'authentification réussie, un jeton est émis par STS pour l'agent.  
  
2. L'agent envoie ce jeton émis par STS au service WCF.  
  
3. Le service WCF qui prend en charge les revendications est configuré pour approuver STS et les jetons qu'il émet. Le service WCF qui prend en charge les revendications utilise WIF pour valider le jeton et l'analyser. Les développeurs utilisent l’API WIF et les types appropriés, par exemple **ClaimsPrincipal**, pour les besoins de l’application, tels que l’implémentation de l’autorisation pour cette dernière.  
  
 À partir de la version .NET 4.5, WIF fait partie du package .NET Framework. Le fait d’avoir les classes WIF directement disponibles dans l’infrastructure permet une intégration plus profonde de l’identité basée sur les revendications dans .NET, facilitant ainsi l’utilisation des revendications. Avec WIF 4.5, vous n'avez pas besoin d'installer de composant hors plage pour démarrer le développement d'applications Web qui prennent en charge les revendications. Les classes WIF sont maintenant réparties sur plusieurs assemblys, les principaux étant System.Security.Claims, System.IdentityModel et System.IdentityModel.Services.  
  
 STS est un service qui émet des jetons en cas de réussite de l'authentification. Microsoft propose deux STS standard compatibles :  
  
- [Active Directory Federation Services (ADFS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure Access Control Service (ACS)](https://docs.microsoft.com/previous-versions/azure/azure-services/hh147631(v=azure.100))
  
 AD FS 2.0 fait partie de Windows Server R2 et peut être utilisé comme un STS pour les scénarios sur site. Azure Active Directory Access Control (également appelé Service de contrôle d'accès ou ACS) est un service cloud proposé dans le cadre de Microsoft Azure. À des fins de test ou à titre éducatif, vous pouvez également utiliser d'autres STS pour générer des applications qui prennent en charge les revendications. Par exemple, vous pouvez utiliser le développement STS Local qui fait partie de la [Identity and Access Tool pour Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) qui est disponible gratuitement en ligne.  
  
 Pour générer votre premier service WCF prenant en charge les revendications à l’aide de WIF, consultez [How To : Activer WIF pour une Application de Service Web WCF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Voir aussi

- [Prise en main de WIF](../../../docs/framework/security/getting-started-with-wif.md)
