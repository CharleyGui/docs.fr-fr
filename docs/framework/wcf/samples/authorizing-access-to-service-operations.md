---
title: Authorizing Access to Service Operations
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 3097c86f50a75dec8a649ca4e1edd2511a046ca8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585530"
---
# <a name="authorizing-access-to-service-operations"></a>Authorizing Access to Service Operations
Cet exemple montre comment utiliser [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) pour permettre l’utilisation de l' <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut pour autoriser l’accès aux opérations de service. Cet exemple est basé sur l’exemple [prise en main](getting-started-sample.md) . Le service et le client sont configurés à l’aide du [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . L' `mode` attribut de [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) a été défini sur `Message` et `clientCredentialType` a été défini sur `Windows` . L'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliqué à chaque méthode de service et utilisé afin de restreindre l'accès à chaque opération. L'appelant doit être un administrateur Windows pour pouvoir accéder à chaque opération.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le fichier de configuration de service utilise [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) pour définir l' `principalPermissionMode` attribut :  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Affecter au `principalPermissionMode` la valeur `UseWindowsGroups` permet d'utiliser l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> en fonction des noms de groupe Windows.  
  
 L'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> est appliqué à chaque opération, indiquant que l'appelant doit appartenir à un groupe Administrateurs Windows, tel qu'illustré dans l'exemple de code suivant.  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Le client parvient à communiquer avec chaque opération s'il s'exécute sous un compte appartenant à un groupe Administrateurs. Dans le cas contraire, l'accès aux opérations lui sera refusé. Faites l'expérience de ce genre d'échec en exécutant le client sous un compte n'appartenant pas à un groupe Administrateurs. Appuyez sur ENTER dans la fenêtre de console pour arrêter le client.  
  
 Les services peuvent être informés des échecs d'autorisation en implémentant un <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Consultez [extension du contrôle sur la gestion des erreurs et la création de rapports](extending-control-over-error-handling-and-reporting.md) pour plus d’informations sur l’implémentation de `IErrorHandler` .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
