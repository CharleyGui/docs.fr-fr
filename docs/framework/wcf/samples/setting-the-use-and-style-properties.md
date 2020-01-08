---
title: Définition des exemples de propriétés use et style
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: 36111aa05680fb8b369cde6b42d22c9c3b8474ad
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345130"
---
# <a name="setting-the-use-and-style-properties"></a>Setting the Use and Style Properties

Cet exemple illustre comment utiliser les propriétés Use et Style des attributs <xref:System.ServiceModel.XmlSerializerFormatAttribute> et <xref:System.ServiceModel.DataContractFormatAttribute>. Ces propriétés affectent la manière dont les messages sont mis en forme. Par défaut, la propriété de style, en fonction de laquelle le corps des messages est mis en forme, a pour valeur <xref:System.ServiceModel.OperationFormatStyle.Document>. Ces paramètres peuvent être spécifiés dans les contrats de service ou d'opération.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

La propriété de style <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> détermine la manière dont les métadonnées WSDL du service sont mises en forme. Cette propriété peut avoir les valeurs suivantes : <xref:System.ServiceModel.OperationFormatStyle.Document> et <xref:System.ServiceModel.OperationFormatStyle.Rpc>. RPC signifie que la représentation WSDL des messages échangés pour une opération contient des paramètres propres à un appel de procédure distante. Voici un exemple.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

Avec le style <xref:System.ServiceModel.OperationFormatStyle.Document>, la représentation WSDL contient un élément unique qui représente le document échangé pour une opération, tel qu'illustré dans l'exemple suivant.

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

La propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> détermine la mise en forme des messages. Les valeurs possibles de cette propriété sont <xref:System.ServiceModel.OperationFormatUse.Literal> et <xref:System.ServiceModel.OperationFormatUse.Encoded>. Sa valeur par défaut est <xref:System.ServiceModel.OperationFormatUse.Literal>. Cette dernière valeur signifie que le message correspond à une instance littérale du schéma dans le WSDL, tel qu'illustré dans l'exemple document/littéral suivant.

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

Encoded signifie que les schémas en WSDL sont des spécifications abstraites encodées selon les règles trouvées dans SOAP 1.1, section 5. Voici un exemple de document RPC/Encoded.

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

Le profil WS-I Basic Profile 1.0 ne permet pas d'utiliser <xref:System.ServiceModel.OperationFormatUse.Encoded>. Vous devez uniquement utiliser ce profil lorsque requis par les services hérités. Le format de message `Encoded` est disponible uniquement lorsque le sérialiseur XmlSerializer est utilisé.

Pour vous permettre de voir les messages envoyés et reçus, cet exemple est basé sur le [suivi et la journalisation des messages](tracing-and-message-logging.md). La configuration du service et le code source ont été modifiés pour activer le suivi et l'enregistrement des messages et permettre leur utilisation. En outre, la liaison <xref:System.ServiceModel.WSHttpBinding> a été configurée sans mode de sécurité. Les messages enregistrés peuvent donc être affichés dans un format non chiffré. Les journaux de suivi résultants (System. ServiceModel. E2E et message. log) doivent être affichés à l’aide de l' [outil Service Trace Viewer (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Les suivis sont configurés de sorte à être créés dans le dossier C:\LOGS. Créez ce dossier avant d’exécuter l’exemple. Pour afficher le contenu d’un message dans l’outil Trace Viewer, sélectionnez **messages** dans les volets de gauche et de droite de l’outil.

Dans le contrat de service défini par le code suivant, la propriété <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> a la valeur <xref:System.ServiceModel.OperationFormatUse> et le format du corps du message au lieu d'avoir la valeur par défaut <xref:System.ServiceModel.OperationFormatStyle> a la valeur <xref:System.ServiceModel.OperationFormatStyle.Document>.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc, 
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

Pour se rendre compte des différences existant entre les paramètres <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> et <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A>, modifiez-les au niveau du service, régénérez le client, exécutez l'exemple, puis examinez le fichier c:\logs\message.logs à l'aide de l'outil Service Trace Viewer. Observez également l’impact sur les métadonnées en affichant `http://localhost/ServiceModelSamples/service.svc?wsdl`. En principe, les métadonnées des services sont réparties sur plusieurs pages. La page WSDL principale contient les liaisons WSDL, mais les `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` d’affichage pour observer les définitions des messages.

## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Créez un répertoire C:\LOGS pour l'enregistrement des messages. Accordez à l'utilisateur des droits d'accès en écriture au service réseau pour ce répertoire.

3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

4. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
