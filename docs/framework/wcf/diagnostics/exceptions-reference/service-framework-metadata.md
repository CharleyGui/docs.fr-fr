---
title: Métadonnées de l'infrastructure de service
ms.date: 03/30/2017
ms.assetid: 76afc73a-0770-4084-93f3-6701a757911e
ms.openlocfilehash: 4133e758cde79294432ca501a10ed7ff20821954
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255765"
---
# <a name="service-framework-metadata"></a>Métadonnées de l'infrastructure de service

Cette rubrique répertorie toutes les exceptions générées par les métadonnées d'infrastructure de service.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|AsyncEndCalledOnWrongChannel|Une méthode End asynchrone a été appelée sur le canal incorrect.|  
|AsyncEndCalledWithAnIAsyncResult|Une méthode End asynchrone a été appelée avec un IAsyncResult à partir d'une méthode Begin différente.|  
|AttemptedToGetContractTypeForButThatTypeIs1|Tentative d’obtenir le type de contrat pour le spécifié. Le type n’est pas un ServiceContract et n’hérite pas d’un ServiceContract.|  
|CannotHaveTwoOperationsWithTheSameName3|Deux opérations dans le même contrat ne peuvent pas avoir le même nom. Les méthodes spécifiées du type spécifié ne respectent pas cette règle. Modifiez le nom d'une des opérations en modifiant le nom de la méthode ou en utilisant la propriété Name de l'attribut OperationContractAttribute.|  
|CannotInheritTwoOperationsWithTheSameName3|Impossible d'hériter de deux opérations différentes portant le même nom. L'opération spécifiée des contrats spécifiés violent cette règle. Modifiez le nom d'une des opérations en modifiant le nom de la méthode ou en utilisant la propriété Name de l'attribut OperationContractAttribute.|  
|CantCreateChannelWithManualAddressing|Impossible de créer un canal pour un contrat qui requiert une demande/réponse et une liaison qui requiert l'adressage manuel mais prend en charge uniquement la communication duplex.|  
|DuplicateBehavior1|La valeur ne peut pas être ajoutée à la collection. La collection contient déjà un élément du même type spécifié. Cette collection ne prend en charge qu’une seule instance de chaque type.|  
|InAContractInheritanceHierarchyIfParentHasCallbackChildMustToo|Étant donné que le contrat de service de base spécifié a un contrat de rappel spécifié, le contrat de service dérivé spécifié doit également spécifier le type spécifié ou un type dérivé comme contrat de rappel.|  
|InvalidAsyncBeginMethodSignatureForMethod2|La signature de méthode Begin asynchrone est non valide pour la méthode spécifiée dans le type d'élément ServiceContract spécifié. Votre méthode Begin doit prendre un élément AsyncCallback et un objet pour ses deux derniers arguments et renvoyer un élément IAsyncResult.|  
|InvalidAsyncEndMethodSignatureForMethod2|La signature de méthode End asynchrone est non valide pour la méthode spécifiée dans le type d'élément ServiceContract spécifié. Votre méthode End doit prendre un élément IAsyncResult comme dernier argument.|  
|MessagePropertiesArraySize0|Le tableau passé n'a pas suffisamment d'espace pour contenir toutes les propriétés contenues dans cette collection.|  
|OneWayAndFaultsIncompatible2|La méthode spécifiée dans le type spécifié est marquée avec IsOneWay=true et déclare un ou plusieurs attributs FaultContractAttributes. Les méthodes monodirectionnelles ne peuvent pas déclarer d'attributs FaultContractAttributes. Définissez IsOneWay à « false » ou supprimez les attributs FaultContractAttributes.|  
|UnsupportedWSDLOnlyOneMessage|Web Services Description Language non pris en charge. Une seule une partie de message est prise en charge pour les messages d'erreur. Ce message d'erreur fait référence à plusieurs parties de message. Si vous avez un accès en édition au fichier WSDL, vous pouvez résoudre le problème en supprimant les parties de messages superflues de telle sorte que le message d'erreur ne fasse référence qu'à une seule partie.|  
|UnsupportedWSDLTheFault|Web Services Description Language non pris en charge. La partie du message d'erreur doit faire référence à un élément. Ce message d'erreur ne fait pas référence à un élément. Si vous avez un accès en édition au document WSDL, vous pouvez résoudre le problème en faisant référence à un élément de schéma à l'aide de l'attribut « element ».|  
|WsdlImportErrorDependencyDetail|Une erreur s'est produite lors de l'important du spécifié dont dépend l'autre valeur spécifiée. Le Xpath est également spécifié.|  
|XsdMissingRequiredAttribute1|Attribut requis spécifié manquant.|
