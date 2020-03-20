---
title: Types obsolètes dans le .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 4.5, obsolete types
- types, obsolete in .NET Framework 4.5
- obsolete types [.NET Framework]
ms.assetid: e636d024-0fac-45eb-b721-25a8c0ceca8f
ms.openlocfilehash: b7932a553f39e1f1da2a3946878d6224099da8da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802685"
---
# <a name="obsolete-types-in-the-net-framework"></a>Types obsolètes dans le .NET Framework

<a name="introduction"></a> Les tableaux de cet article listent les types obsolètes dans .NET Framework 4.5 et .NET Framework 4.6, organisés par assembly. Utilisez les liens suivants pour consulter la liste des types obsolètes et des alternatives recommandées dans chaque assembly. Ces types étant obsolètes, tous leurs membres le sont également. Pour obtenir la liste des membres obsolètes supplémentaires dans la bibliothèque de classes .NET Framework, consultez [Membres obsolètes](obsolete-members.md).

- [Types obsolètes dans les assemblages de systèmes](#obsolete_types_in_system_assemblies)

  - [mscorlib.dll](#mscorlib)

  - [System.Core.dll](#Core)

  - [System.Data.dll](#data)

  - [System.Data.OracleClient.dll](#oracleclient)

  - [System.Design.dll](#design)

  - [System.dll](#system)

  - [System.EnterpriseServices.dll](#enterpriseservices)

  - [System.Net.dll](#net)

  - [System.ServiceModel.dll](#servicemodel)

  - [System.Web.dll](#web)

  - [System.Web.Mobile.dll](#mobile)

  - [System.Workflow.Activities.dll](#workflow_activities)

  - [System.Workflow.ComponentModel.dll](#workflow_componentmodel)

  - [System.Workflow.Runtime.dll](#workflow_runtime)

  - [System.WorkflowServices.dll](#workflowservices)

  - [System.Xaml.dll](#xaml)

  - [System.Xml.dll](#xml)

  - [WindowsBase.dll](#WindowsBase)

- [Types obsolètes dans les assemblages Microsoft](#obsolete_types_in_microsoft_assemblies)

  - [IEHost.dll et IEExec.exe](#IEHost)

  - [Microsoft.Build.Engine.dll](#Engine)

  - [Microsoft.JScript.dll](#jscript)

  - [Microsoft.VisualBasic.Compatibility.dll](#VBCompat)

  - [Microsoft.VisualBasic.Compatibility.Data.dll](#VBCompatData)

  - [Microsoft.VisualC.dll](#visualc)

<a name="obsolete_types_in_system_assemblies"></a>

## <a name="obsolete-types-in-system-assemblies"></a>Types obsolètes dans les assemblys système

Les tableaux suivants répertorient les types qui ont été déclarés obsolètes dans les assemblys système. Ces assemblys sont utilisés pour le développement d’applications à usage général qui ciblent le .NET Framework.

<a name="mscorlib"></a>

### <a name="assembly-mscorlibdll"></a>Assembly : mscorlib.dll

|Type|Message|
|----------|-------------|
|<xref:System.ExecutionEngineException?displayProperty=nameWithType>|Ce type indiquait une erreur irrécupérable non spécifiée dans l'exécution. Étant donné que l'exécution ne déclenche plus cette exception, ce type est devenu obsolète.|
|<xref:System.Collections.CaseInsensitiveHashCodeProvider?displayProperty=nameWithType>|Utilisez plutôt <xref:System.StringComparer?displayProperty=nameWithType>.|
|<xref:System.Collections.IHashCodeProvider?displayProperty=nameWithType>|Utilisez plutôt <xref:System.Collections.IEqualityComparer?displayProperty=nameWithType>.|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|La classe <xref:System.Configuration.Assemblies.AssemblyHash> a été déconseillée.|
|<xref:System.Diagnostics.Contracts.Internal.ContractHelper?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5. Au lieu de cela, utilisez la classe <xref:System.Runtime.CompilerServices.ContractHelper?displayProperty=nameWithType> dans l’espace de noms System.Runtime.CompilerServices.|
|<xref:System.Reflection.Emit.UnmanagedMarshal?displayProperty=nameWithType>|Une autre API est disponible : émettez l'attribut personnalisé <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.BIND_OPTS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.BIND_OPTS?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.BINDPTR?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.BINDPTR?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.CALLCONV?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.CALLCONV?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.CONNECTDATA?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.CONNECTDATA?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.DESCKIND?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.DESCKIND?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.DISPPARAMS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.DISPPARAMS?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.ELEMDESC?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.ELEMDESC?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.EXCEPINFO?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.EXCEPINFO?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.FILETIME?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.FILETIME?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.FUNCDESC?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.FUNCDESC?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.FUNCFLAGS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.FUNCFLAGS?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.FUNCKIND?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.FUNCKIND?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType>|Cet attribut est déprécié et sera supprimé dans une version ultérieure.|
|<xref:System.Runtime.InteropServices.IDispatchImplType?displayProperty=nameWithType>|Le <xref:System.Runtime.InteropServices.IDispatchImplAttribute?displayProperty=nameWithType> est déconseillé.|
|<xref:System.Runtime.InteropServices.IDLDESC?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IDLDESC?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.IDLFLAG?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IDLFLAG?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.IMPLTYPEFLAGS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IMPLTYPEFLAGS?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.INVOKEKIND?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.INVOKEKIND?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.LIBFLAGS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.LIBFLAGS?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.PARAMDESC?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.PARAMDESC?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.PARAMFLAG?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.PARAMFLAG?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.SetWin32ContextInIDispatchAttribute?displayProperty=nameWithType>|Cet attribut est déprécié. Les domaines d'application ne respectent plus les limites de contexte d'activation dans les appels IDispatch.|
|<xref:System.Runtime.InteropServices.STATSTG?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.STATSTG?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.SYSKIND?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.SYSKIND?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.TYPEATTR?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.TYPEATTR?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.TYPEDESC?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.TYPEDESC?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.TYPEFLAGS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.TYPEFLAGS?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.TYPEKIND?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.TYPEKIND?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.TYPELIBATTR?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.TYPELIBATTR?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIBindCtx?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IBindCtx?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPoint?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIConnectionPointContainer?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnectionPoints?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IEnumConnectionPoints?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIEnumConnections?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IEnumConnections?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIEnumMoniker?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IEnumMoniker?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIEnumString?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IEnumString?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIEnumVARIANT?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIMoniker?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IMoniker?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIPersistFile?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IPersistFile?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIRunningObjectTable?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IRunningObjectTable?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMIStream?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMITypeComp?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.ITypeComp?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMITypeInfo?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.UCOMITypeLib?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.ITypeLib?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.VARDESC?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.VARDESC?displayProperty=nameWithType> à la place.|
|<xref:System.Runtime.InteropServices.VARFLAGS?displayProperty=nameWithType>|Utilisez <xref:System.Runtime.InteropServices.ComTypes.VARFLAGS?displayProperty=nameWithType> à la place.|
|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalScope> est utilisé uniquement pour la compatibilité de transparence du .NET 2.0.|
|<xref:System.Security.SecurityTreatAsSafeAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityTreatAsSafeAttribute> est utilisé uniquement pour la compatibilité de transparence du .NET 2.0. Utilisez plutôt le <xref:System.Security.SecuritySafeCriticalAttribute?displayProperty=nameWithType>.|
|<xref:System.Security.Policy.FirstMatchCodeGroup?displayProperty=nameWithType>|Ce type est obsolète et sera supprimé dans une prochaine version du .NET Framework.|
|<xref:System.Security.Policy.PermissionRequestEvidence?displayProperty=nameWithType>|La sécurité déclarative au niveau de l'assembly est obsolète et n'est plus appliquée par le CLR par défaut.|
|<xref:System.Security.Policy.UnionCodeGroup?displayProperty=nameWithType>|Ce type est obsolète et sera supprimé dans une prochaine version du .NET Framework.|

[Retour au début](#introduction)

<a name="Core"></a>

### <a name="assembly-systemcoredll"></a>Assembly : System.Core.dll

|Type|Message|
|----------|-------------|
|<xref:System.Runtime.CompilerServices.ExecutionScope?displayProperty=nameWithType>|L'utilisation de ce type génère une erreur du compilateur.<br /><br /> N'utilisez pas ce type.|

[Retour au début](#introduction)

<a name="data"></a>

### <a name="assembly-systemdatadll"></a>Assembly : System.Data.dll

|Type|Message|
|----------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute> a été déprécié.|
|<xref:System.Data.PropertyAttributes?displayProperty=nameWithType>|<xref:System.Data.PropertyAttributes> a été déprécié.|
|<xref:System.Data.TypedDataSetGenerator?displayProperty=nameWithType>|La classe <xref:System.Data.TypedDataSetGenerator> sera supprimée dans une version ultérieure. Utilisez <xref:System.Data.Design.TypedDataSetGenerator?displayProperty=nameWithType> dans System.Design.dll.|
|<xref:System.Xml.XmlDataDocument?displayProperty=nameWithType>|La classe <xref:System.Xml.XmlDataDocument> sera supprimée dans une version ultérieure.|

[Retour au début](#introduction)

<a name="oracleclient"></a>

### <a name="assembly-systemdataoracleclientdll"></a>Assembly : System.Data.OracleClient.dll

|Type|Message|
|----------|-------------|
|<xref:System.Data.OracleClient.OracleClientFactory?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleClientFactory> a été déprécié.|
|<xref:System.Data.OracleClient.OracleCommand?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommand> a été déprécié.|
|<xref:System.Data.OracleClient.OracleCommandBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleCommandBuilder> a été déprécié.|
|<xref:System.Data.OracleClient.OracleConnection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnection> a été déprécié.|
|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder> a été déprécié.|
|<xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleDataAdapter> a été déprécié.|
|<xref:System.Data.OracleClient.OraclePermission?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermission> a été déprécié.|
|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OraclePermissionAttribute?displayProperty=nameWithType> a été déprécié.|

[Retour au début](#introduction)

<a name="design"></a>

### <a name="assembly-systemdesigndll"></a>Assembly : System.Design.dll

|Type|Message|
|----------|-------------|
|<xref:System.ComponentModel.Design.LocalizationExtenderProvider?displayProperty=nameWithType>|Cette classe a été déconseillée. Utilisez <xref:System.ComponentModel.Design.Serialization.CodeDomLocalizationProvider?displayProperty=nameWithType> à la place.|
|<xref:System.Web.UI.Design.DataBindingCollectionConverter?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée étant donné que la modification DataBindings est lancée via un <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> au lieu de la grille des propriétés.|
|<xref:System.Web.UI.Design.DataBindingCollectionEditor?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée étant donné que la modification DataBindings est lancée via un <xref:System.ComponentModel.Design.DesignerActionList?displayProperty=nameWithType> au lieu de la grille des propriétés.|
|<xref:System.Web.UI.Design.IControlDesignerBehavior?displayProperty=nameWithType>|L'alternative recommandée consiste à utiliser <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> et <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IHtmlControlDesignerBehavior?displayProperty=nameWithType>|L'alternative recommandée consiste à utiliser <xref:System.Web.UI.Design.IControlDesignerTag?displayProperty=nameWithType> et <xref:System.Web.UI.Design.IControlDesignerView?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingFrame?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée, car la modification de modèle est gérée dans <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Pour prendre en charge la modification de modèle, exposez les données de modèle dans la propriété <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> et appelez <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormReferenceManager?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Web.UI.Design.WebFormsReferenceManager?displayProperty=nameWithType>. Le <xref:System.Web.UI.Design.WebFormsReferenceManager> contient des fonctionnalités supplémentaires et permet une meilleure extensibilité. Pour obtenir le <xref:System.Web.UI.Design.WebFormsReferenceManager>, utilisez la propriété `RootDesigner.ReferenceManager` à partir de votre <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.IWebFormsDocumentService?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType>. Le <xref:System.Web.UI.Design.WebFormsRootDesigner> contient des fonctionnalités supplémentaires et permet une meilleure extensibilité. Pour obtenir le <xref:System.Web.UI.Design.WebFormsRootDesigner>, utilisez la propriété <xref:System.Web.UI.Design.ControlDesigner.RootDesigner%2A> à partir de votre <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ITemplateEditingService?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée, car la modification de modèle est gérée dans <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Pour prendre en charge la modification de modèle, exposez les données de modèle dans la propriété <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> et appelez <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.ReadWriteControlDesigner?displayProperty=nameWithType>|L'alternative recommandée consiste à utiliser <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> étant donné qu'il emploie un <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> pour la modification du contenu. Les zones du concepteur permettent de mieux contrôler le contenu qui est modifié.|
|<xref:System.Web.UI.Design.TemplateEditingService?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée, car la modification de modèle est gérée dans <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Pour prendre en charge la modification de modèle, exposez les données de modèle dans la propriété <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> et appelez <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.TemplateEditingVerb?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée, car la modification de modèle est gérée dans <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>. Pour prendre en charge la modification de modèle, exposez les données de modèle dans la propriété <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> et appelez <xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.WebControls.CalendarAutoFormatDialog?displayProperty=nameWithType>|L'utilisation de ce type n'est pas recommandée étant donné que la boîte de dialogue Mise en forme automatique est lancée par l'hôte concepteur. La liste des mises en forme automatiques disponibles est exposée sur le <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> dans la propriété <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType>.|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|L'alternative recommandée consiste à utiliser <xref:System.Web.UI.Design.WebControls.PanelContainerDesigner?displayProperty=nameWithType> étant donné qu'il emploie un <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType> pour la modification du contenu. Les zones du concepteur permettent de mieux contrôler le contenu qui est modifié.|

[Retour au début](#introduction)

<a name="system"></a>

### <a name="assembly-systemdll"></a>Assembly : System.dll

|Type|Message|
|----------|-------------|
|<xref:System.ComponentModel.IComNativeDescriptorHandler?displayProperty=nameWithType>|Cette interface a été déconseillée. Ajoutez à la place un <xref:System.ComponentModel.TypeDescriptionProvider?displayProperty=nameWithType> pour gérer le type <xref:System.ComponentModel.TypeDescriptor.ComObjectType%2A?displayProperty=nameWithType>.|
|<xref:System.ComponentModel.RecommendedAsConfigurableAttribute?displayProperty=nameWithType>|Utilisez plutôt <xref:System.ComponentModel.SettingsBindableAttribute?displayProperty=nameWithType> pour employer le nouveau modèle de paramètres.|
|<xref:System.ComponentModel.Design.Serialization.RootDesignerSerializerAttribute?displayProperty=nameWithType>|Cet attribut est déprécié. Utilisez <xref:System.ComponentModel.Design.Serialization.DesignerSerializerAttribute?displayProperty=nameWithType> à la place.|
|<xref:System.Diagnostics.DiagnosticsConfigurationHandler?displayProperty=nameWithType>|Cette classe a été déconseillée.|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|Cette classe a été déconseillée. Utilisez plutôt des compteurs de performance via la classe <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>.|
|<xref:System.Net.GlobalProxySelection?displayProperty=nameWithType>|Cette classe a été déconseillée. Utilisez plutôt <xref:System.Net.WebRequest.DefaultWebProxy%2A?displayProperty=nameWithType> pour accéder au proxy global par défaut et le paramétrer. Utilisez la valeur 'null' au lieu de <xref:System.Net.GlobalProxySelection.GetEmptyWebProxy%2A?displayProperty=nameWithType>.|
|<xref:System.Net.Sockets.SocketClientAccessPolicyProtocol?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|

[Retour au début](#introduction)

<a name="enterpriseservices"></a>

### <a name="assembly-systementerpriseservicesdll"></a>Assembly : System.EnterpriseServices.dll

|Type|Message|
|----------|-------------|
|<xref:System.EnterpriseServices.RegistrationHelperTx?displayProperty=nameWithType>|La classe <xref:System.EnterpriseServices.RegistrationHelperTx> a été déconseillée.|

[Retour au début](#introduction)

<a name="net"></a>

### <a name="assembly-systemnetdll"></a>Assembly : System.Net.dll

|Type|Message|
|----------|-------------|
|<xref:System.Net.INetworkProgress?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.IUnsafeWebRequestCreate?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.NetworkProgressChangedEventArgs?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.UiSynchronizationContext?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.Sockets.HttpPolicyDownloaderProtocol?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.Sockets.SecurityCriticalAction?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.Sockets.SocketPolicy?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.Sockets.UdpAnySourceMulticastClient?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Net.Sockets.UdpSingleSourceMulticastClient?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|

[Retour au début](#introduction)

<a name="servicemodel"></a>

### <a name="assembly-systemservicemodeldll"></a>Assembly : System.ServiceModel.dll

|Type|Message|
|----------|-------------|
|<xref:System.ServiceModel.NetPeerTcpBinding?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|
|<xref:System.ServiceModel.Channels.HttpCookieContainerBindingElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Ce type est obsolète. Pour activer la classe <xref:System.Net.CookieContainer> HTTP, utilisez la propriété `AllowCookies` sur la liaison HTTP ou sur <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.|
|<xref:System.ServiceModel.Channels.PeerCustomResolverBindingElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|
|<xref:System.ServiceModel.Channels.PeerTransportBindingElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingCollectionElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|
|<xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|
|<xref:System.ServiceModel.Configuration.PeerTransportElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|
|<xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> La fonctionnalité de canal pair est obsolète et sera supprimée dans le futur.|

[Retour au début](#introduction)

<a name="web"></a>

### <a name="assembly-systemwebdll"></a>Assembly : System.Web.dll

|Type|Message|
|----------|-------------|
|<xref:System.Web.Configuration.PassportAuthentication?displayProperty=nameWithType>|Ce type est obsolète. Le produit d’authentification Passport n’est plus pris en charge et a été remplacé par [Microsoft Account](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Mail.MailAttachment?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Net.Mail.Attachment?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailEncoding?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Net.Mime.TransferEncoding?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailFormat?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Net.Mail.MailMessage.IsBodyHtml%2A?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.MailPriority?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Net.Mail.MailPriority?displayProperty=nameWithType>.|
|<xref:System.Web.Mail.SmtpMail?displayProperty=nameWithType>|L'alternative recommandée est <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>.|
|<xref:System.Web.Security.PassportAuthenticationEventArgs?displayProperty=nameWithType>|Ce type est obsolète. Le produit d’authentification Passport n’est plus pris en charge et a été remplacé par [Microsoft Account](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportAuthenticationEventHandler?displayProperty=nameWithType>|Ce type est obsolète. Le produit d’authentification Passport n’est plus pris en charge et a été remplacé par [Microsoft Account](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportAuthenticationModule?displayProperty=nameWithType>|Ce type est obsolète. Le produit d’authentification Passport n’est plus pris en charge et a été remplacé par [Microsoft Account](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportIdentity?displayProperty=nameWithType>|Ce type est obsolète. Le produit d’authentification Passport n’est plus pris en charge et a été remplacé par [Microsoft Account](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.Security.PassportPrincipal?displayProperty=nameWithType>|Ce type est obsolète. Le produit d’authentification Passport n’est plus pris en charge et a été remplacé par [Microsoft Account](https://account.microsoft.com/account/Account?destrt=home-index)|
|<xref:System.Web.UI.ObjectConverter?displayProperty=nameWithType>|L'alternative recommandée consiste à utiliser <xref:System.Convert?displayProperty=nameWithType> et <xref:System.String.Format%2A?displayProperty=nameWithType>.|

[Retour au début](#introduction)

<a name="mobile"></a>

### <a name="assembly-systemwebmobiledll"></a>Assembly : System.Web.Mobile.dll

|Type|Message|
|----------|-------------|
|<xref:System.Web.Mobile.CookielessData?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElement?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFilterElementCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.DeviceFiltersSection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.ErrorHandlerModule?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileCapabilities?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileDeviceCapabilitiesSectionHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileErrorInfo?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.Mobile.MobileFormsAuthentication?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileDesigner?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.IMobileWebFormServices?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.MobileResource?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataFieldConverter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.Design.MobileControls.Converters.DataMemberConverter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.AdRotator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Alignment?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ArrayListCollectionBase?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BaseValidator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.BooleanOption?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Calendar?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Command?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CommandFormat?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CompareValidator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Constants?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElement?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlElementCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ControlPager?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.CustomValidator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DesignerAdapterAttribute?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElement?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceElementCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceOverridableAttribute?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecific?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoice?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificChoiceTemplateContainer?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.DeviceSpecificControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ErrorFormatterPage?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontInfo?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FontSize?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Form?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.FormMethod?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IControlAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Image?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IObjectListFieldCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.IPageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ItemPager?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ITemplateable?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Label?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Link?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.List?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListCommandEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDataBindEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListDecoration?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ListSelectType?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralLink?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralText?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextContainerControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LiteralTextControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.LoadItemsEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControl?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileControlsSectionHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItem?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileListItemType?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobilePage?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileTypeNameConverter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.MobileUserControl?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectList?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommand?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListCommandEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListDataBindEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListField?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListFieldCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItem?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListItemCollection?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListSelectEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventArgs?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListShowCommandsEventHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListTitleAttribute?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ObjectListViewMode?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagedControl?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PagerStyle?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Panel?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PanelControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PersistNameAttribute?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.PhoneCall?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RangeValidator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RegularExpressionValidator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.RequiredFieldValidator?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.SelectionList?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Style?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheet?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.StyleSheetControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TemplateContainer?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBox?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextBoxControlBuilder?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextControl?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextView?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.TextViewElement?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.ValidationSummary?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Wrapping?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCalendarAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlCommandAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlFormAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlImageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlLinkAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlMobileTextWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlPhoneCallAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlSelectionListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ChtmlTextBoxAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.ControlAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCalendarAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlCommandAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlControlAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlFormAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlImageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLabelAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLinkAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlLiteralTextAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlMobileTextWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlObjectListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPanelAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlPhoneCallAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlSelectionListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextBoxAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlTextViewAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidationSummaryAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.HtmlValidatorAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MobileTextWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.MultiPartWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlMobileTextWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.UpWmlPageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCalendarAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlCommandAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlControlAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlFormAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlImageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLabelAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLinkAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlLiteralTextAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlMobileTextWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlObjectListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPanelAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPhoneCallAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlPostFieldType?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlSelectionListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextBoxAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlTextViewAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidationSummaryAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.WmlValidatorAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.Doctype?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.StyleSheetLocation?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCalendarAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCommandAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlControlAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlCssHandler?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlFormAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlImageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLabelAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLinkAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlLiteralTextAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlMobileTextWriter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlObjectListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPageAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPanelAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlPhoneCallAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlSelectionListAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextBoxAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlTextViewAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidationSummaryAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|
|<xref:System.Web.UI.MobileControls.Adapters.XhtmlAdapters.XhtmlValidatorAdapter?displayProperty=nameWithType>|L'assembly System.Web.Mobile.dll est déconseillé et ne doit plus être utilisé. Pour plus d’informations sur le développement d’applications mobiles ASP.NET, consultez [ASP.NET pour les mobiles](/aspnet/mobile/overview).|

[Retour au début](#introduction)

<a name="workflow_activities"></a>

### <a name="assembly-systemworkflowactivitiesdll"></a>Assembly : System.Workflow.Activities.dll

|Type|Message|
|----------|-------------|
|Tous les types dans l'espace de noms <xref:System.Workflow.Activities?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.Activities.Configuration.ActiveDirectoryRoleFactoryConfiguration?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.Activities.Rules.RuleActionTrackingEvent?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.Activities.Rules.RuleConditionReference?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.Activities.Rules.RuleSetReference?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|

[Retour au début](#introduction)

<a name="workflow_componentmodel"></a>

### <a name="assembly-systemworkflowcomponentmodeldll"></a>Assembly : System.Workflow.ComponentModel.dll

|Type|Message|
|----------|-------------|
|Tous les types dans l'espace de noms <xref:System.Workflow.ComponentModel> sauf <xref:System.Workflow.ComponentModel.GetValueOverride?displayProperty=nameWithType> et <xref:System.Workflow.ComponentModel.SetValueOverride?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.ComponentModel.Compiler> sauf <xref:System.Workflow.ComponentModel.Compiler.ValidationError?displayProperty=nameWithType> et <xref:System.Workflow.ComponentModel.Compiler.ValidationErrorCollection?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.ComponentModel.Design> sauf <xref:System.Workflow.ComponentModel.Design.ConnectorEventHandler>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializationManager?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityCodeDomSerializer?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityMarkupSerializer?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivitySurrogateSelector?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.ActivityTypeCodeDomSerializer?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.CompositeActivityMarkupSerializer?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|<xref:System.Workflow.ComponentModel.Serialization.DependencyObjectCodeDomSerializer?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|

[Retour au début](#introduction)

<a name="workflow_runtime"></a>

### <a name="assembly-systemworkflowruntimedll"></a>Assembly : System.Workflow.Runtime.dll

|Type|Message|
|----------|-------------|
|<xref:System.Activities.Statements.Interop?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br />Les types Workflow Foundation 3.0 sont dépréciés. Utilisez à la place les types Workflow 4.0 de <xref:System.Activities>\*.|
|<xref:System.Activities.Tracking.InteropTrackingRecord?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br />Les types Workflow Foundation 3.0 sont dépréciés. Utilisez à la place les types Workflow 4.0 de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.Runtime>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.Runtime.Configuration>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.Runtime.DebugEngine> sauf <xref:System.Workflow.Runtime.DebugEngine.DebugEngineCallback>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.Runtime.Hosting> sauf <xref:System.Workflow.Runtime.Hosting.WorkflowCommitWorkBatchService.CommitWorkBatchCallback>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.Runtime.Tracking>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types System.Workflow.\* sont dépréciés. Utilisez à la place les nouveaux types de <xref:System.Activities>\*.|

[Retour au début](#introduction)

<a name="workflowservices"></a>

### <a name="assembly-systemworkflowservicesdll"></a>Assembly : System.WorkflowServices.dll

|Type|Message|
|----------|-------------|
|<xref:System.ServiceModel.WorkflowServiceHost?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Activation.WorkflowServiceHostFactory?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Activities.Description.WorkflowRuntimeEndpoint?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Configuration.ExtendedWorkflowRuntimeServiceElementCollection?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Configuration.PersistenceProviderElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Configuration.WorkflowRuntimeElement?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Description.DurableOperationAttribute?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Description.DurableServiceAttribute?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Description.PersistenceProviderBehavior?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Description.UnknownExceptionAction?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Description.WorkflowRuntimeBehavior?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Dispatcher.DurableOperationContext?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.InstanceLockException?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.InstanceNotFoundException?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.LockingPersistenceProvider?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.PersistenceException?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProvider?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.PersistenceProviderFactory?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|Tous les types dans l'espace de noms <xref:System.Workflow.Activities?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|
|<xref:System.Workflow.Runtime.Hosting.ChannelManagerService?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> Les types WF 3 sont dépréciés. Utilisez à la place les nouveaux types WF 4 de <xref:System.Activities>\*.|

[Retour au début](#introduction)

<a name="xaml"></a>

### <a name="assembly-systemxamldll"></a>Assembly : System.Xaml.dll

|Type|Message|
|----------|-------------|
|<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute?displayProperty=nameWithType>|Cela n'est pas utilisé par l'analyseur XAML. Regardez <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>.|

[Retour au début](#introduction)

<a name="xml"></a>

### <a name="assembly-systemxmldll"></a>Assembly : System.Xml.dll

|Type|Message|
|----------|-------------|
|<xref:System.Xml.IApplicationResourceStreamResolver?displayProperty=nameWithType>|D'abord déconseillé dans .NET Framework 4.5.<br /><br /> L'utilisation de ce type génère une erreur du compilateur.<br /><br /> Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Xml.Schema.XmlSchemaCollection?displayProperty=nameWithType>|Utilisez <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> pour la compilation et la validation de schémas.|
|<xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType>|Utilisez plutôt une classe <xref:System.Xml.XmlReader?displayProperty=nameWithType> créée par la méthode <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> à l'aide des classes <xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType> appropriées.|
|<xref:System.Xml.XmlXapResolver?displayProperty=nameWithType>|L'utilisation de ce type génère une erreur du compilateur. Cette API prend en charge l'infrastructure .NET Framework et n'est pas destinée à être directement utilisée à partir de votre code.|
|<xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType>|Cette classe a été déconseillée. Utilisez plutôt <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType>.|

[Retour au début](#introduction)

<a name="WindowsBase"></a>

### <a name="assembly-windowsbasedll"></a>Assembly : WindowsBase.dll

|Type|Message|
|----------|-------------|
|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType>|<xref:System.Windows.Markup.IReceiveMarkupExtension?displayProperty=nameWithType> a été déprécié. Cette interface n'est plus utilisée.|

[Retour au début](#introduction)

<a name="obsolete_types_in_microsoft_assemblies"></a>

## <a name="obsolete-types-in-microsoft-assemblies"></a>Types obsolètes dans les assemblys Microsoft

Les sections suivantes répertorient les types obsolètes dans les assemblys Microsoft. Il s'agit d'assemblys ayant un usage spécial, comme les assemblys qui ciblent un langage individuel (par exemple, Microsoft.JScript.dll ou Microsoft.VisualC.dll).

<a name="IEHost"></a>

### <a name="assembly-iehostdll-and-ieexecexe"></a>Assembly : IEHost.dll et IEExec.exe

Les assemblys IEHost.dll et IEExec.exe ont été supprimés du .NET Framework. Tous leurs types et leurs membres sont obsolètes, et ne sont pas pris en charge à partir de .NET Framework 4. Ces assemblys ont été utilisés pour héberger des contrôles Windows Forms et exécuter des exécutables dans Internet Explorer. Les alternatives recommandées incluent ClickOnce, des applications du navigateur XAML (XBAP) et Microsoft Silverlight.

[Retour au début](#introduction)

<a name="Engine"></a>

### <a name="assembly-microsoftbuildenginedll"></a>Assembly : Microsoft.Build.Engine.dll

|Type|Message|
|----------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|Cette classe a été déconseillée. Utilisez à la place <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> de l’assembly *Microsoft.Build*.|
|<xref:Microsoft.Build.BuildEngine.Project?displayProperty=nameWithType>|Cette classe a été déconseillée. Utilisez à la place <xref:Microsoft.Build.Evaluation.ProjectCollection?displayProperty=nameWithType> de l’assembly *Microsoft.Build*.|

[Retour au début](#introduction)

<a name="jscript"></a>

### <a name="assembly-microsoftjscriptdll"></a>Assembly : Microsoft.JScript.dll

|Type|Message|
|----------|-------------|
|<xref:Microsoft.JScript.Vsa.BaseVsaEngine?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.BaseVsaSite?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.BaseVsaStartup?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaCodeItem?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaEngine?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaError?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaGlobalItem?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItem?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaItems?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaPersistSite?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaReferenceItem?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.IJSVsaSite?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.JSVsaError?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.JSVsaException?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemFlag?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.JSVsaItemType?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.ResInfo?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|
|<xref:Microsoft.JScript.Vsa.VsaEngine?displayProperty=nameWithType>|Ce type a été déprécié dans Visual Studio 2005 et il n’existe pas de fonctionnalité de remplacement. Pour obtenir une aide supplémentaire, consultez la documentation de <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType>.|

[Retour au début](#introduction)

<a name="VBCompat"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydll"></a>Assembly : Microsoft.VisualBasic.Compatibility.dll

Pour plus d’informations sur la migration à partir de Visual Basic 6, consultez [Centre de ressources Visual Basic 6.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-basic-6/visual-basic-6.0-documentation).

|Type|Message|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseControlArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseOcxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ButtonArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CheckedListBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ColorDialogArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ComboBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBox?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DirListBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBox?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DriveListBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBox?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FileListBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FixedLengthString?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FontDialogArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.FormShowConstants?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.GroupBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.HScrollBarArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ImageListArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LabelArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListBoxItem?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ListViewArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.LoadResConstants?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MaskedTextBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MenuItemArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MouseButtonConstants?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.OpenFileDialogArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PanelArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PictureBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.PrintDialogArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ProgressBarArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RadioButtonArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.RichTextBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SaveFileDialogArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ScaleMode?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ShiftConstants?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusBarArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.StatusStripArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.Support?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TabControlArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TextBoxArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TimerArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolBarArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ToolStripMenuItemArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.TreeViewArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.VScrollBarArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebBrowserArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClass?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassContainingClassNotOptional?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassCouldNotFindEvent?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemCannotBeCurrentWebItem?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassNextItemRespondNotFound?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassUserWebClassNameNotOptional?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebClassFileNameNotOptional?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebClassWebItemNotValid?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItem?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemAssociatedWebClassNotOptional?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemClosingTagNotFound?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadEmbeddedResource?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemCouldNotLoadTemplateFile?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNameNotOptional?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemNoTemplateSpecified?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemTooManyNestedTags?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.WebItemUnexpectedErrorReadingTemplateFile?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ZOrderConstants?displayProperty=nameWithType>|Ce membre est obsolète.|

[Retour au début](#introduction)

<a name="VBCompatData"></a>

### <a name="assembly-microsoftvisualbasiccompatibilitydatadll"></a>Assembly : Microsoft.VisualBasic.Compatibility.Data.dll

|Type|Message|
|----------|-------------|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.BOFActionEnum?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EndOfRecordsetDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.EOFActionEnum?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.ErrorDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchCompleteDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FetchProgressDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.FieldChangeCompleteDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.MoveCompleteDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.OrientationEnum?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordChangeCompleteDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.RecordsetChangeCompleteDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeFieldDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillChangeRecordsetDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODC.WillMoveDelegate?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.ADODCArray?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BaseDataEnvironment?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.BindingCollectionEnumerator?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.CONNECTDATA?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBBINDING?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBCOLUMNINFO?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBID?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBinding?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBindingCollection?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBKINDENUM?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.DBPROPIDSET?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IAccessor?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IChapteredRowset?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IColumnsInfo?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPoint?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IConnectionPointContainer?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormat?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IDataFormatDisp?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnectionPoints?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IEnumConnections?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPosition?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowPositionChange?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowset?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetChange?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetIdentity?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetInfo?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.IRowsetNotify?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBinding?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.MBindingCollection?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.SRDescriptionAttribute?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UGUID?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UNAME?displayProperty=nameWithType>|Ce membre est obsolète.|
|<xref:Microsoft.VisualBasic.Compatibility.VB6.UpdateMode?displayProperty=nameWithType>|Ce membre est obsolète.|

[Retour au début](#introduction)

<a name="visualc"></a>

### <a name="assembly-microsoftvisualcdll"></a>Assembly : Microsoft.VisualC.dll

|Type|Message|
|----------|-------------|
|<xref:Microsoft.VisualC.DebugInfoInPDBAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.DecoratedNameAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.IsConstModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.IsCXXReferenceModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.IsLongModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.IsSignedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.IsVolatileModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.MiscellaneousBitsAttribute?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.NeedsCopyConstructorModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|
|<xref:Microsoft.VisualC.NoSignSpecifiedModifier?displayProperty=nameWithType>|Microsoft.VisualC.dll est un assembly obsolète et existe uniquement à des fins de compatibilité descendante.|

## <a name="see-also"></a>Voir aussi

- [Éléments obsolètes dans la bibliothèque de classes](whats-obsolete.md)
- [Membres obsolètes](obsolete-members.md)
