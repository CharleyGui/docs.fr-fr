---
title: 'Exemple : Gestion des exceptions pendant la liaison de données'
ms.date: 03/30/2017
ms.assetid: bd63ed96-9853-46dc-ade5-7bd1b0f39110
ms.openlocfilehash: 399bd1af9ef25eca9cdfe1e13fdc4c01021babcd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251072"
---
# <a name="example-handling-exceptions-when-binding-data"></a>Exemple : Gestion des exceptions pendant la liaison de données

> [!NOTE]
> Cette rubrique fait référence à .NET Native Developer Preview, qui correspond à la version préliminaire du logiciel. Vous pouvez télécharger la préversion sur le [site web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (inscription nécessaire).  
  
 L’exemple suivant montre comment résoudre une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) qui est levée lorsqu’une application compilée avec la chaîne d’outils .net Native tente de lier des données. Voici les informations sur l'exception :  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:
App.ViewModels.MainPageVM  
```  
  
 Voici la pile des appels associée :  
  
```output
Reflection::Execution::ReflectionDomainSetupImplementation.CreateNonInvokabilityException+0x238  
Reflection::Core::ReflectionDomain.CreateNonInvokabilityException+0x2e  
Reflection::Core::Execution::ExecutionEnvironment.+0x316  
System::Reflection::Runtime::PropertyInfos::RuntimePropertyInfo.GetValue+0x1cb  
System::Reflection::PropertyInfo.GetValue+0x22  
System::Runtime::InteropServices::WindowsRuntime::CustomPropertyImpl.GetValue+0x42  
App!$66_Interop::McgNative.Func_IInspectable_IInspectable+0x158  
App!$66_Interop::McgNative::__vtable_Windows_UI_Xaml_Data__ICustomProperty.GetValue__STUB+0x46  
Windows_UI_Xaml!DirectUI::PropertyProviderPropertyAccess::GetValue+0x3f
Windows_UI_Xaml!DirectUI::PropertyAccessPathStep::GetValue+0x31
Windows_UI_Xaml!DirectUI::PropertyPathListener::ConnectPathStep+0x113  
```  
  
## <a name="what-was-the-app-doing"></a>Que faisait l’application ?  

 À la base de la pile, les frames de l' <xref:Windows.UI.Xaml?displayProperty=nameWithType> espace de noms indiquent que le moteur de rendu XAML était en cours d’exécution.   L'utilisation de la méthode <xref:System.Reflection.PropertyInfo.GetValue%2A?displayProperty=nameWithType> indique une recherche basée sur la réflexion de la valeur d'une propriété sur le type dont les métadonnées ont été supprimées.  
  
 La première étape pour fournir une directive de métadonnées consisterait à ajouter des métadonnées `serialize` pour le type afin que ses propriétés soient toutes accessibles :  
  
```xml  
<Type Name="App.ViewModels.MainPageVM" Serialize="Required Public" />  
```  
  
## <a name="is-this-an-isolated-case"></a>S'agit-il d'un cas isolé ?  

 Dans ce scénario, si la liaison de données contient des métadonnées incomplètes pour un `ViewModel`, cela peut également être le cas pour d'autres.  Si le code est structuré de façon à ce que les modèles d'affichage de l'application se trouvent tous dans l'espace de noms `App.ViewModels`, vous pouvez utiliser une directive runtime plus générale :  
  
```xml  
<Namespace Name="App.ViewModels " Serialize="Required Public" />  
```  
  
## <a name="could-the-code-be-rewritten-to-not-use-reflection"></a>Le code peut-il être réécrit de manière à ne pas utiliser la réflexion ?  

 Comme la liaison de données repose sur la réflexion, modifier le code pour éviter la réflexion est impossible.  
  
 Toutefois, certains procédés permettent de spécifier le `ViewModel` pour la page XAML afin que la chaîne d'outils associe les liaisons de propriété au type approprié au moment de la compilation et conserve les métadonnées sans utiliser de directive runtime.  Par exemple, vous pouvez appliquer l' <xref:Windows.UI.Xaml.Data.BindableAttribute?displayProperty=nameWithType> attribut sur les propriétés. Ainsi, le compilateur XAML génère les informations de recherche nécessaires et évite la présence d'une directive runtime dans le fichier Default.rd.xml.  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started-with-net-native.md)
- [Exemple : Résolution des problèmes de programmation dynamique](example-troubleshooting-dynamic-programming.md)
