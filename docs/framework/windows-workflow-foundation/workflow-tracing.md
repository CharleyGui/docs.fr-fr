---
title: Suivi de workflow
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: b5a8f650edfdade4a18999c5e7af38ca72112122
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273878"
---
# <a name="workflow-tracing"></a>Suivi de workflow

Le suivi de workflow offre une méthode de capture des informations de diagnostic à l'aide d'écouteurs de suivi .NET Framework. Le suivi peut être activé si un problème a été détecté dans l'application, puis désactivé de nouveau une fois le problème résolu. Deux méthodes s'offrent à vous pour activer le suivi de débogage pour les flux de travail. Vous pouvez le configurer à l'aide de la visionneuse de suivi d'événements ou bien utiliser l'objet <xref:System.Diagnostics> pour envoyer des événements de suivi à un fichier.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Activation du suivi de débogage dans ETW  

 Pour activer le suivi à l'aide d'ETW, activez le canal de débogage dans l'Observateur d'événements :  
  
1. Dans l'Observateur d'événements, naviguez vers le nœud des journaux d'analyse et de débogage.  
  
2. Dans l’arborescence de observateur d’événements, accédez à **observateur d’événements >journaux des applications et des services->serveur d’applications Microsoft >Windows->-applications**. Cliquez avec le bouton droit sur **serveur d’applications-applications** , puis sélectionnez **affichage->afficher les journaux d’analyse et de débogage**. Cliquez avec le bouton droit sur **Debug** , puis sélectionnez **activer le journal**.  
  
3. Lorsqu'un flux de travail exécute le débogage et qu'un suivi est émis vers le canal de débogage ETW, le suivi peut être affiché dans l'Observateur d'événements. Accédez à **observateur d’événements >journaux des applications et des services->serveur d’applications Microsoft >Windows->-applications**. Cliquez avec le bouton droit sur **Debug** , puis sélectionnez **Actualiser**.  
  
4. La taille de la mémoire tampon de trace analytique par défaut est de 4 kilo-octet (Ko) seulement. Il est recommandé d'augmenter la taille à 32 Ko. Pour ce faire, procédez comme suit.  
  
    1. Exécutez la commande suivante dans le répertoire de l'infrastructure actuelle (par exemple, C:\Windows\Microsoft.NET\Framework\v4.0.21203) : `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2. Remplacez la \<bufferSize> valeur dans le fichier Windows. ApplicationServer. applications. Man par 32.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. Exécutez la commande suivante dans le répertoire de l'infrastructure actuelle (par exemple, C:\Windows\Microsoft.NET\Framework\v4.0.21203) : `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
> Si vous utilisez le profil client .NET Framework 4, vous devez d’abord enregistrer le manifeste ETW en exécutant la commande suivante à partir du répertoire .NET Framework 4 : `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Activation du suivi de débogage à l'aide de System.Diagnostics  

 Ces écouteurs peuvent être configurés dans le fichier App.config de l'application de workflow ou le fichier Web.config pour un service de workflow. Dans cet exemple, un <xref:System.Diagnostics.TextWriterTraceListener> est configuré pour enregistrer les informations de traçage dans le fichier MyTraceLog.txt dans le répertoire actif.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Analyse Windows Server App Fabric](/previous-versions/appfabric/ee677251(v=azure.10))
- [Surveillance des applications avec application Fabric](/previous-versions/appfabric/ee677276(v=azure.10))
