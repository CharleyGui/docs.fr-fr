---
title: 'Procédure : mapper des HRESULT et des exceptions'
description: Passez en revue la façon de mapper les valeurs HRESULT retournées à partir des méthodes COM aux exceptions levées par les méthodes .NET. Le Runtime gère la transition entre COM et .NET.
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
ms.openlocfilehash: ff20dc50e1a5f1ce87a4a40691110d247b52e479
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794695"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Procédure : mapper des HRESULT et des exceptions

Les méthodes COM signalent les erreurs en retournant des HRESULT ; les méthodes .NET les signalent en levant des exceptions. Le runtime gère la transition entre les deux. Chaque classe d’exception dans le .NET Framework est mappée à une valeur HRESULT.

 Les classes d’exceptions définies par l’utilisateur peuvent spécifier la valeur HRESULT appropriée. Ces classes d’exception peuvent modifier dynamiquement la valeur HRESULT à retourner lorsque l’exception est générée en définissant le `HResult` champ sur l’objet exception. Des informations supplémentaires sur l’exception sont fournies au client via l' `IErrorInfo` interface, qui est implémentée sur l’objet .net dans le processus non managé.

 Si vous créez une classe qui étend `System.Exception` , vous devez définir le champ HRESULT pendant la construction. Sinon, la classe de base assigne la valeur HRESULT. Vous pouvez mapper de nouvelles classes d’exceptions à un HRESULT existant en fournissant la valeur dans le constructeur de l’exception.

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

 Vous pouvez rencontrer un programme (écrit dans n’importe quel langage de programmation) qui utilise à la fois un code managé et un code non managé en même temps. Par exemple, le marshaleur personnalisé dans l’exemple de code suivant utilise la `Marshal.ThrowExceptionForHR(int HResult)` méthode pour lever une exception avec une valeur HRESULT spécifique. La méthode examine la valeur HRESULT et génère le type d’exception approprié. Par exemple, le HRESULT dans le fragment de code suivant génère `ArgumentException` .

```cpp
CMyClass::MethodThatThrows
{
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);
}
```

 Le tableau suivant fournit les mappages courants de HRESULT à sa classe d’exception comparable dans .NET. Les valeurs HRESULT sans mappages explicites sont mappées à `COMException` . Le mappage complet mis à jour se trouve dans le [référentiel dotnet/Runtime](https://github.com/dotnet/runtime/blob/master/src/coreclr/vm/rexcep.h).

|HRESULT|Exception .NET|
|-------------|--------------------|
|`COR_E_APPLICATION`|`ApplicationException`|
|`COR_E_ARGUMENT` ou `E_INVALIDARG`|`ArgumentException`|
|`COR_E_ARGUMENTOUTOFRANGE`|`ArgumentOutOfRangeException`|
|`COR_E_ARITHMETIC or ERROR_ARITHMETIC_OVERFLOW`|`ArithmeticException`|
|`COR_E_ARRAYTYPEMISMATCH`|`ArrayTypeMismatchException`|
|`COR_E_BADIMAGEFORMAT or ERROR_BAD_FORMAT`|`BadImageFormatException`|
|`COR_E_DIRECTORYNOTFOUND or ERROR_PATH_NOT_FOUND`|`DirectoryNotFoundException`|
|`COR_E_DIVIDEBYZERO`|`DivideByZeroException`|
|`COR_E_DUPLICATEWAITOBJECT`|`DuplicateWaitObjectException`|
|`COR_E_ENDOFSTREAM`|`EndOfStreamException`|
|`COR_E_ENTRYPOINTNOTFOUND`|`EntryPointNotFoundException`|
|`COR_E_EXCEPTION`|`Exception`|
|`COR_E_EXECUTIONENGINE`|`ExecutionEngineException`|
|`COR_E_FIELDACCESS`|`FieldAccessException`|
|`COR_E_FILENOTFOUND or ERROR_FILE_NOT_FOUND`|`FileNotFoundException`|
|`COR_E_FORMAT`|`FormatException`|
|`COR_E_INDEXOUTOFRANGE`|`IndexOutOfRangeException`|
|`COR_E_INVALIDCAST or E_NOINTERFACE`|`InvalidCastException`|
|`COR_E_INVALIDFILTERCRITERIA`|`InvalidFilterCriteriaException`|
|`COR_E_INVALIDOPERATION`|`InvalidOperationException`|
|`COR_E_IO`|`IOException`|
|`COR_E_MEMBERACCESS`|`AccessException`|
|`COR_E_METHODACCESS`|`MethodAccessException`|
|`COR_E_MISSINGFIELD`|`MissingFieldException`|
|`COR_E_MISSINGMANIFESTRESOURCE`|`MissingManifestResourceException`|
|`COR_E_MISSINGMEMBER`|`MissingMemberException`|
|`COR_E_MISSINGMETHOD`|`MissingMethodException`|
|`COR_E_NOTFINITENUMBER`|`NotFiniteNumberException`|
|`E_NOTIMPL`|`NotImplementedException`|
|`COR_E_NOTSUPPORTED`|`NotSupportedException`|
|`COR_E_NULLREFERENCE orE_POINTER`|`NullReferenceException`|
|`COR_E_OUTOFMEMORY or`<br /><br /> `E_OUTOFMEMORY`|`OutOfMemoryException`|
|`COR_E_OVERFLOW`|`OverflowException`|
|`COR_E_PATHTOOLONG or ERROR_FILENAME_EXCED_RANGE`|`PathTooLongException`|
|`COR_E_RANK`|`RankException`|
|`COR_E_REFLECTIONTYPELOAD`|`ReflectionTypeLoadException`|
|`COR_E_SECURITY`|`SecurityException`|
|`COR_E_SERIALIZATION`|`SerializationException`|
|`COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW`|`StackOverflowException`|
|`COR_E_SYNCHRONIZATIONLOCK`|`SynchronizationLockException`|
|`COR_E_SYSTEM`|`SystemException`|
|`COR_E_TARGET`|`TargetException`|
|`COR_E_TARGETINVOCATION`|`TargetInvocationException`|
|`COR_E_TARGETPARAMCOUNT`|`TargetParameterCountException`|
|`COR_E_THREADINTERRUPTED`|`ThreadInterruptedException`|
|`COR_E_THREADSTATE`|`ThreadStateException`|
|`COR_E_TYPELOAD`|`TypeLoadException`|
|`COR_E_TYPEINITIALIZATION`|`TypeInitializationException`|
|`COR_E_VERIFICATION`|`VerificationException`|

 Pour récupérer des informations d’erreur étendues, le client managé doit examiner les champs de l’objet exception généré. Pour que l’objet exception fournisse des informations utiles sur une erreur, l’objet COM doit implémenter l' `IErrorInfo` interface. Le runtime utilise les informations fournies par `IErrorInfo` pour initialiser l’objet exception.

 Si l’objet COM ne prend pas en charge `IErrorInfo` , le runtime Initialise un objet exception avec les valeurs par défaut. Le tableau suivant répertorie chaque champ associé à un objet exception et identifie la source des informations par défaut lorsque l’objet COM prend en charge `IErrorInfo` .

 Notez que le runtime ignore parfois un `HRESULT` si le thread comporte un `IErrorInfo`.  Ce comportement peut se présenter si `HRESULT` et `IErrorInfo` ne représentent pas la même erreur.

|Champ d’exception|Source d’informations à partir de COM|
|---------------------|------------------------------------|
|`ErrorCode`|HRESULT retourné à l’issue de l’appel.|
|`HelpLink`|Si `IErrorInfo->HelpContext` est différent de zéro, la chaîne est formée par concaténation `IErrorInfo->GetHelpFile` et « # » et `IErrorInfo->GetHelpContext` . Dans le cas contraire, la chaîne est retournée à partir de `IErrorInfo->GetHelpFile` .|
|`InnerException`|Toujours une référence null ( `Nothing` dans Visual Basic).|
|`Message`|Chaîne retournée par `IErrorInfo->GetDescription` .|
|`Source`|Chaîne retournée par `IErrorInfo->GetSource` .|
|`StackTrace`|Trace de la pile.|
|`TargetSite`|Nom de la méthode ayant retourné la valeur HRESULT qui a échoué.|

 Les champs d’exception, tels que `Message` , et, ne `Source` `StackTrace` sont pas disponibles pour le `StackOverflowException` .

## <a name="see-also"></a>Voir aussi

- [Interopérabilité COM avancée](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Exceptions](../../standard/exceptions/index.md)
