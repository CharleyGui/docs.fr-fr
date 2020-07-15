---
title: Considérations sur la sécurité et la communication à distance
description: En savoir plus sur les considérations de sécurité en ce qui concerne la communication à distance, qui vous permet de configurer un appel transparent entre des domaines d’application, des processus ou des ordinateurs.
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
ms.openlocfilehash: 019773b19eaca2e4364fb79c40fdb923093d4e7e
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309363"
---
# <a name="security-and-remoting-considerations"></a>Considérations sur la sécurité et la communication à distance
La communication à distance vous permet de définir des appels transparents entre des domaines d'application, des processus ou des ordinateurs. Cependant, le parcours de pile de la sécurité d'accès du code ne peut pas traverser des processus ou des limites de machine (il s'applique pourtant entre les domaines d'application du même processus).  
  
 Toute classe accessible à distance (dérivée d'une classe <xref:System.MarshalByRefObject>) doit être responsable de la sécurité. Soit le code ne doit être utilisé que dans des environnements fermés où le code appelant peut faire l'objet d'une confiance implicite, soit des appels de communication à distance doivent être conçus de façon à ne pas soumettre de code protégé à une entrée externe qui pourrait être utilisée à des fins malveillantes.  
  
 En règle générale, vous ne devez jamais exposer de méthodes, de propriétés ou d’événements protégés par un [LinkDemand](link-demands.md) déclaratif et des <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> vérifications de sécurité. Avec la communication à distance, ces contrôles ne sont pas appliqués. D’autres vérifications de sécurité, telles que <xref:System.Security.Permissions.SecurityAction.Demand> , [Assert](using-the-assert-method.md), etc., fonctionnent entre les domaines d’application au sein d’un processus, mais ne fonctionnent pas dans les scénarios inter-processus ou inter-ordinateurs.  
  
## <a name="protected-objects"></a>Objets protégés  
 Certains objets comportent un état de sécurité. Ces objets ne doivent pas être passés à du code non fiable, qui obtiendrait alors des autorisations de sécurité n'entrant pas dans le champ de ses propres autorisations.  
  
 Un exemple consiste à créer un objet <xref:System.IO.FileStream>. Le <xref:System.Security.Permissions.FileIOPermission> est exigé au moment de la création et, en cas de réussite, l'objet de fichier est retourné. Toutefois, si cette référence d'objet est passée au code sans les autorisations de fichier, l'objet pourra lire et écrire dans ce fichier.  
  
 La défense la plus simple pour un tel objet consiste à demander la même **autorisation FileIOPermission** de tout code visant à obtenir la référence d’objet via un élément d’API public.  
  
## <a name="application-domain-crossing-issues"></a>Questions relatives au franchissement de domaine d'application  
 Pour isoler du code dans des environnements d'hébergement managés, il est courant de générer plusieurs domaines d'application enfants dont la stratégie explicite réduit les niveaux d'autorisations pour divers assemblys. Cependant, la stratégie pour ces assemblys reste inchangée dans le domaine d'application par défaut. Si l'un des domaines d'application enfants peut forcer le domaine d'application par défaut à charger un assembly, l'effet de l'isolement du code est perdu et les types dans l'assembly chargé de force pourront exécuter du code à un niveau de confiance plus élevé.  
  
 Un domaine d'application peut forcer un autre domaine d'application à charger un assembly et exécuter le code qu'il contient en appelant un proxy vers un objet hébergé dans l'autre domaine d'application. Pour obtenir un proxy entre domaines d'application, le domaine d'application qui héberge l'objet doit en distribuer un par l'intermédiaire d'un paramètre d'appel de méthode ou d'une valeur de retour. Ou, si le domaine d'application vient d'être créé, le créateur possède un proxy vers l'objet Ou, si le domaine d'application vient d'être créé, le créateur possède un proxy vers l'objet <xref:System.AppDomain> par défaut. Ainsi, pour éviter d’interrompre l’isolement du code, un domaine d’application dont le niveau de confiance est supérieur ne doit pas distribuer de références aux objets marshalés par référence (instances de classes dérivées de <xref:System.MarshalByRefObject>) dans son domaine à des domaines d’application dont les niveaux de confiance sont moindres.  
  
 Généralement, le domaine d'application par défaut crée les domaines d'application enfants avec un objet contrôle dans chacun d'entre eux. L'objet contrôle gère le nouveau domaine d'application et de manière occasionnelle reçoit des instructions du domaine d'application par défaut, mais il ne peut pas en fait contacter le domaine directement. Parfois, le domaine d'application par défaut appelle son proxy vers l'objet contrôle. Cependant, il se peut qu'il y ait des cas où il est nécessaire que l'objet contrôle rappelle dans le domaine d'application par défaut. Dans ces cas, le domaine d’application par défaut passe un objet de rappel marshalé par référence au constructeur de l’objet contrôle. L'objet contrôle est responsable de la protection de ce proxy. Si l’objet de contrôle a placé le proxy sur un champ statique public d’une classe publique ou si le proxy est exposé publiquement, un mécanisme dangereux permettant à un autre code de rappeler le domaine d’application par défaut est ouvert. C'est la raison pour laquelle les objets contrôle sont toujours autorisés de manière implicite à maintenir le proxy privé.  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
