---
title: Autorisations dangereuses et administration de stratégie
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645758"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Autorisations dangereuses et administration de stratégie
Plusieurs des opérations protégées pour lesquelles le .NET Framework fournit des autorisations risquent de permettre le contournement du système de sécurité. Ces autorisations dangereuses doivent être accordées uniquement à du code fiable, et seulement en cas de nécessité. Il n’existe généralement aucune défense contre du code malveillant, si ces autorisations sont accordées.  
  
> [!NOTE]
> Dans le cadre .NET 4, il y a eu d’importants changements au modèle et à la terminologie de la sécurité du cadre .NET. Pour plus d’informations sur ces changements, voir [changements de sécurité](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Les autorisations dangereuses sont expliquées dans le tableau suivant.  
  
|Autorisation|Risque potentiel|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Permet au code managé d’appeler du code non managé, ce qui est souvent dangereux.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|En l’absence de vérification, le code peut tout faire.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Les preuves invalidées peuvent tromper la stratégie de sécurité.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|La modification de la stratégie de sécurité peut permettre de désactiver la sécurité.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|L’utilisation de la sérialisation peut constituer un moyen de contourner les mécanismes d’accessibilité. Pour plus d’informations, consultez [Sécurité et sérialisation](security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|La capacité à définir le principal actuel peut permettre de tromper la sécurité basée sur les rôles.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|La manipulation des threads est dangereuse en raison de l’état de sécurité associé aux threads.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Permet d’utiliser des membres privés pour passer outre les mécanismes d’accessibilité.|  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../standard/security/secure-coding-guidelines.md)
