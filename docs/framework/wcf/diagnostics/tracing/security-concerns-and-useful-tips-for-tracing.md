---
title: Problèmes de sécurité et conseils utiles pour le suivi
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 0a09e387a4f964441f11d07a84bd492345d5b691
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578875"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>Problèmes de sécurité et conseils utiles pour le suivi
Cette rubrique décrit comment empêcher l'exposition des informations sensibles et fournit également des conseils utiles en cas d'utilisation de WebHost.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Utilisation d'un écouteur de suivi personnalisé avec WebHost  
 Si vous écrivez votre propre écouteur de suivi, vous devez savoir que les traces peuvent être perdues dans le cas d'un service hébergé sur le Web. Lorsque WebHost recycle, il arrête le processus en cours pendant qu'un doublon prend la relève. Toutefois, les deux processus doivent encore avoir accès à la même ressource pendant quelques temps, ce qui dépend du type d'écouteur. Dans ce cas, `XmlWriterTraceListener` crée un fichier de suivi pour le deuxième processus, alors que le suivi des événements Windows gère plusieurs processus dans la même session et donne accès au même fichier. Si votre propre écouteur ne fournit pas de fonctionnalités semblables, des traces peuvent être perdues lorsque le fichier est verrouillé par les deux processus.  
  
 Vous devez également savoir qu'un écouteur de suivi personnalisé peut envoyer des traces et des messages sur le câble, par exemple à une base de données distante. En tant que responsable du déploiement d'applications, vous devez configurer les écouteurs personnalisés avec un contrôle d'accès approprié. Vous devez également appliquer un contrôle de sécurité sur toute information personnelle qui peut être exposée à l'emplacement distant.  
  
## <a name="logging-sensitive-information"></a>Enregistrement des informations sensibles  
 Les suivis contiennent des en-têtes de messages lorsqu'un message est dans la portée. Lorsque le suivi est activé, les informations personnelles dans les en-têtes spécifiques à l'application, telles qu'une chaîne de requête, et les informations de corps, telles qu'un numéro de carte de crédit, peuvent devenir visibles dans les journaux. Le responsable du déploiement d'applications est chargé de mettre en vigueur le contrôle d'accès sur les fichiers de configuration et de suivi. Si vous ne souhaitez pas que ce type d'informations soit visible, vous devez désactiver le suivi ou éliminer une partie des données par filtrage si vous souhaitez partager les journaux de suivi.  
  
 Les conseils suivants peuvent vous aider à empêcher que le contenu d'un fichier de suivi ne soit exposé involontairement :  
  
- Assurez-vous que les fichiers journaux sont protégés par des listes de contrôle d'accès dans les scénarios WebHost et à auto-hébergement.  
  
- Choisissez une extension de fichier qui ne peut pas être facilement fournie à l’aide d’une demande Web. Par exemple, l’extension de fichier .xml n’est pas un choix sûr. Vous pouvez vérifier le guide d’administration des services Internet (IIS) pour obtenir une liste des extensions qui peuvent être servies.  
  
- Spécifiez un chemin d’accès absolu pour l’emplacement de fichier journal, qui doit être en dehors du répertoire public vroot WebHost afin d’empêcher qu’il soit accessible par un correspondant externe à l’aide d’un navigateur Web.  
  
 Par défaut, les clés et informations personnelles, telles que le nom d'utilisateur et le mot de passe, ne sont pas enregistrées dans les traces et les messages consignés. Toutefois, un administrateur d'ordinateur peut utiliser l'attribut `enableLoggingKnownPII` dans l'élément `machineSettings` du fichier Machine.config pour autoriser des applications qui s'exécutent sur l'ordinateur à enregistrer des informations d'identification personnelle PII (Personally Identifiable Information) connues comme suit :  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 Un responsable du déploiement d'applications peut ensuite utiliser l'attribut `logKnownPii` dans le fichier App.config ou Web.config pour activer la journalisation PII comme suit :  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 La journalisation PII est uniquement activée lorsque les deux paramètres ont la valeur `true`. La combinaison de deux commutateurs offre la souplesse nécessaire pour enregistrer les informations personnelles connues pour chaque application.  
  
 Sachez que si vous spécifiez plusieurs sources personnalisées dans un fichier de configuration, seuls les attributs de la première sont lus. Les autres sont ignorés. Cela signifie que, pour le fichier App.config suivant, les informations personnelles ne sont pas enregistrées pour les deux sources même si la journalisation PII est explicitement activée pour la deuxième source.  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="false">  
        <listeners>  
           <add name="messages"  
                type="System.Diagnostics.XmlWriterTraceListener"  
                initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
      <source name="System.ServiceModel"
         logKnownPii="true">  
         <listeners>  
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Si l'élément `<machineSettings enableLoggingKnownPii="Boolean"/>` existe en dehors du fichier Machine.config, le système lève un <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Les modifications ne sont effectives qu'au démarrage ou redémarrage de l'application. Un événement est enregistré au démarrage lorsque les deux attributs ont la valeur `true`. Un événement est également enregistré si `logKnownPii` a la valeur `true` mais que `enableLoggingKnownPii` a la valeur `false`.  
  
 Pour plus d’informations sur la journalisation PII, consultez exemple de [verrouillage de sécurité PII](../../samples/pii-security-lockdown.md) .  
  
 L'administrateur d'ordinateur et le responsable du déploiement d'applications doivent observer la plus grande prudence lorsqu'ils utilisent ces deux commutateurs. Si la journalisation PII est activée, les clés de sécurité et les informations personnelles sont enregistrées. Si elle est désactivée, les données sensibles et spécifiques aux applications sont toujours enregistrées dans les corps et en-têtes des messages. Pour une discussion plus approfondie sur la confidentialité et la protection des informations d’identification, consultez [confidentialité des utilisateurs](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 De plus, l'adresse IP de l'expéditeur du message est enregistrée une fois par connexion pour les transports orientés connexion, et une fois par message envoyé par d'autres transports. Cette opération est effectuée sans le consentement de l'expéditeur. Toutefois, cet enregistrement se produit uniquement aux niveaux de suivi Information ou Verbose, qui ne sont pas les niveaux de suivi par défaut ou recommandés dans les environnements de production, hormis pour le débogage en direct.  
  
## <a name="see-also"></a>Voir aussi

- [Suivi](index.md)
