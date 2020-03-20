---
title: 'Comment : mapper des HRESULT et des exceptions'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
ms.openlocfilehash: e186228d1dc9a42ddfe92428f7dfad29a5789095
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181406"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Comment : mapper des HRESULT et des exceptions
Les méthodes COM signalent les erreurs en retournant des HRESULT ; les méthodes .NET les signalent en levant des exceptions. Le runtime gère la transition entre les deux. Chaque classe d’exception dans le .NET Framework est mappée à une valeur HRESULT.  
  
 Les classes d’exceptions définies par l’utilisateur peuvent spécifier la valeur HRESULT appropriée. Ces classes d’exceptions peuvent modifier dynamiquement la valeur HRESULT à retourner quand l’exception est générée par la définition du champ **HResult** sur l’objet exception. Des informations supplémentaires relatives à l’exception sont fournies au client par le biais de l’interface **IErrorInfo**, qui est implémentée sur l’objet .NET dans le processus non managé.  
  
 Si vous créez une classe qui étend **System.Exception**, vous devez définir le champ HRESULT pendant la construction. Sinon, la classe de base assigne la valeur HRESULT. Vous pouvez mapper de nouvelles classes d’exceptions à un HRESULT existant en fournissant la valeur dans le constructeur de l’exception.  
  
 Notez que le runtime ignore parfois un `HRESULT` si le thread comporte un `IErrorInfo`.  Ce comportement peut se présenter si `HRESULT` et `IErrorInfo` ne représentent pas la même erreur.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Pour créer une classe d’exception et la mapper à un HRESULT  
  
1. Utilisez le code suivant pour créer une classe d’exception appelée `NoAccessException` et mappez-la à la valeur HRESULT `E_ACCESSDENIED`.  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 Vous pouvez rencontrer un programme (écrit dans n’importe quel langage de programmation) qui utilise à la fois un code managé et un code non managé en même temps. Par exemple, le marshaleur personnalisé dans l’exemple de code suivant utilise la méthode **Marshal.ThrowExceptionForHR(int HResult)** pour lever une exception avec une valeur HRESULT spécifique. La méthode examine la valeur HRESULT et génère le type d’exception approprié. Par exemple, dans le fragment de code suivant, HRESULT génère **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Le tableau suivant fournit le mappage complet de chaque HRESULT à sa classe d’exception comparable dans le .NET Framework.  
  
|HRESULT|Exception .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT or E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC or ERROR_ARITHMETIC_OVERFLOW**|**ArithmeticException**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT or ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException (CoreException)**|  
|**NTE_FAIL**|**CryptographicException**|  
|**COR_E_DIRECTORYNOTFOUND or ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR_E_EXCEPTION**|**Exception**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND or ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST or E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException (en anglais)**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY or**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG or ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**RemotingException**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR_E_SYSTEM**|**Systemexception**|  
|**COR_E_TARGET**|**TargetException**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Tous les autres HRESULT**|**COMException**|  
  
 Pour récupérer des informations d’erreur étendues, le client managé doit examiner les champs de l’objet exception généré. Pour que l’objet exception fournisse des informations utiles sur une erreur, l’objet COM doit implémenter l’interface **IErrorInfo**. Le runtime utilise les informations fournies par **IErrorInfo** pour initialiser l’objet exception.  
  
 Si l’objet COM ne prend pas en charge **IErrorInfo**, le runtime initialise un objet exception avec les valeurs par défaut. Le tableau suivant répertorie chaque champ associé à un objet exception et identifie la source des informations par défaut quand l’objet COM prend en charge **IErrorInfo**.  
  
 Notez que le runtime ignore parfois un `HRESULT` si le thread comporte un `IErrorInfo`.  Ce comportement peut se présenter si `HRESULT` et `IErrorInfo` ne représentent pas la même erreur.  
  
|Champ d’exception|Source d’informations à partir de COM|  
|---------------------|------------------------------------|  
|**Errorcode**|HRESULT retourné à l’issue de l’appel.|  
|**HelpLink**|Si **IErrorInfo->HelpContext** est différent de zéro, la chaîne est formée en concaténant **IErrorInfo->GetHelpFile**, « # » et **IErrorInfo->GetHelpContext**. Sinon, la chaîne est retournée depuis **IErrorInfo->GetHelpFile**.|  
|**InnerException**|Toujours une référence nulle **(Rien** dans Visual Basic).|  
|**Message**|Chaîne retournée depuis **IErrorInfo->GetDescription**.|  
|**source**|Chaîne retournée depuis **IErrorInfo->GetSource**.|  
|**StackTrace (en)**|Trace de la pile.|  
|**TargetSite**|Nom de la méthode ayant retourné la valeur HRESULT qui a échoué.|  
  
 Les champs d’exception, tels que **Message**, **Source** et **StackTrace** ne sont pas disponibles pour **StackOverflowException**.  
  
## <a name="see-also"></a>Voir aussi

- [Interopérabilité COM avancée](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Exceptions](../../standard/exceptions/index.md)
