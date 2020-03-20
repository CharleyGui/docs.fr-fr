---
title: Problèmes de sécurité relatifs à la journalisation des messages
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: bb1a6ab84ceba27b398d397b4407a55aa02c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185775"
---
# <a name="security-concerns-for-message-logging"></a>Problèmes de sécurité relatifs à la journalisation des messages
Cette rubrique contient des instructions permettant de protéger des données sensibles afin d'éviter qu'elles ne soient visibles dans les journaux des messages et de protéger les événements générés par l'enregistrement des messages.  
  
## <a name="security-concerns"></a>Problèmes de sécurité  
  
### <a name="logging-sensitive-information"></a>Enregistrement des informations sensibles  
 Windows Communication Foundation (WCF) ne modifie aucune donnée dans les en-têtes et le corps spécifiques à l’application. WCF ne suit pas non plus les informations personnelles dans les en-têtes spécifiques à l’application ou les données corporelles.  
  
 Lorsque la journalisation des messages est activée, les informations personnelles contenues dans les en-têtes spécifiques aux applications (par exemple, une chaîne de requête) et les données relatives au corps (par exemple, un numéro de carte de crédit) peuvent être visibles dans les journaux. Le responsable du déploiement d'applications est chargé d'appliquer le contrôle d'accès sur les fichiers journaux et de configuration. Si vous ne souhaitez pas que ce type d'informations soit visible, vous devez désactiver la journalisation, ou filtrer une partie des données en cas de partage des journaux.  
  
 Les conseils suivants vous permettent d'éviter l'exposition involontaire du contenu d'un fichier journal :  
  
- Assurez-vous que les fichiers journaux sont protégés par des listes de contrôle d'accès (ACL, Access Control Lists), à la fois dans les scénarios auto-hébergés et hébergés sur le Web.  
  
- Choisissez une extension de fichier qui ne peut pas être facilement fournie à l’aide d’une demande Web. Par exemple, l’extension de fichier .xml n’est pas un choix sûr. Consultez le guide d'administration IIS (Internet Information Services) pour obtenir la liste des extensions qui peuvent être fournies.  
  
- Spécifiez un chemin d'accès absolu pour l'emplacement de fichier journal, qui doit se trouver hors du répertoire public de la racine virtuelle de l'hôte Web afin d'empêcher tout intervenant externe d'y accéder à l'aide d'un navigateur Web.  
  
 Par défaut, les clés et informations personnelles, telles que le nom d'utilisateur et le mot de passe, ne sont pas enregistrées dans les traces et les messages consignés. Toutefois, un administrateur d'ordinateur peut utiliser l'attribut `enableLoggingKnownPII` dans l'élément `machineSettings` du fichier Machine.config pour autoriser les applications s'exécutant sur l'ordinateur à enregistrer les informations personnelles connues. La configuration suivante montre comment procéder :  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
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
  
> [!IMPORTANT]
> Dans [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)], les indicateurs `logEntireMessage` et `logKnownPii` doivent également être définis avec la valeur `true` dans le fichier Web.config ou App.config pour activer la journalisation PII, comme indiqué dans l'exemple suivant `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
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
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Si l'élément `<machineSettings enableLoggingKnownPii="Boolean"/>` existe en dehors du fichier Machine.config, le système lève un <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Les modifications ne sont effectives qu'au démarrage ou redémarrage de l'application. Un événement est enregistré au démarrage lorsque les deux attributs ont la valeur `true`. Un événement est également enregistré si `logKnownPii` a la valeur `true` mais que `enableLoggingKnownPii` a la valeur `false`.  
  
 L'administrateur d'ordinateur et le responsable du déploiement d'applications doivent observer la plus grande prudence lorsqu'ils utilisent ces deux commutateurs. Si la journalisation PII est activée, les clés de sécurité et les informations personnelles sont enregistrées. Si elle est désactivée, les données sensibles et spécifiques aux applications sont toujours enregistrées dans les corps et en-têtes des messages. Pour une discussion plus approfondie sur la vie privée et la protection de l’IPI contre l’exposition, voir [la confidentialité des utilisateurs](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
> [!CAUTION]
> Les informations personnelles ne sont pas masquées dans les messages malformés. Les messages de ce type sont consignés en l'état sans aucune modification. Les attributs précédemment mentionnés n'ont aucun effet sur cela.  
  
### <a name="custom-trace-listener"></a>Écouteur de suivi personnalisé  
 L'ajout d'un écouteur de suivi personnalisé sur la source de suivi de journalisation des messages est un privilège qui doit être réservé à l'administrateur. En effet, des écouteurs personnalisés malveillants peuvent être configurés pour envoyer des messages à distance, ce qui se traduit par la divulgation d'informations sensibles. De plus, si vous configurez un écouteur personnalisé pour envoyer des messages sur le câble, par exemple vers une base de données distante, vous devez appliquer le contrôle d'accès approprié sur les journaux de messages de l'ordinateur distant.  
  
## <a name="events-triggered-by-message-logging"></a>Événements déclenchés par la journalisation des messages  
 La section suivante répertorie tous les événements émis par la journalisation des messages.  
  
- Journalisation des messages activée : cet événement est émis lorsque la journalisation des messages est activée dans la configuration ou via WMI. Le contenu de l'événement est "La journalisation des messages a été activée. Des informations sensibles peuvent être enregistrées en clair, même si elles ont été chiffrées sur le câble, par exemple, corps de message."  
  
- Journalisation des messages désactivée : cet événement est émis lorsque la journalisation des messages est désactivée via WMI. Le contenu de l'événement est "La journalisation des messages a été activée."  
  
- Enregistrement des informations personnelles connues activé : cet événement est émis lorsque l'enregistrement des données personnelles connues est activé. Cela se `enableLoggingKnownPii` produit lorsque `machineSettings` l’attribut dans l’élément `true`du fichier `logKnownPii` Machine.config est configuré à , et l’attribut de l’élément `source` dans le fichier App.config ou Web.config est réglé à `true`.  
  
- Enregistrement des informations personnelles connues activé non autorisé : cet événement est émis lorsque l'enregistrement des informations personnelles connues n'est pas autorisé. Cela se `logKnownPii` produit lorsque `source` l’attribut de l’élément dans le fichier `true`App.config ou `machineSettings` Web.config est configuré `false`à , mais l’attribut `enableLoggingKnownPii` dans l’élément du fichier Machine.config est réglé à . Aucune exception n'est levée.  
  
 Ces événements peuvent être affichés dans l'outil Observateur d'événements fourni avec Windows. Pour plus d’informations à ce sujet, voir [Event Logging](./event-logging/index.md).  
  
## <a name="see-also"></a>Voir aussi

- [Journalisation des messages](message-logging.md)
- [Problèmes de sécurité et conseils utiles pour le suivi](./tracing/security-concerns-and-useful-tips-for-tracing.md)
