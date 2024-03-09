+++
title = 'Hello World!'
date = 2024-03-09T00:20:14-03:00
draft = false
+++

The Builder Design Pattern is used when the object you need to create requires more complex logic to be instantiated.

Take a Email object as an example - you have multiple properties that need to be defined: title, message, importance status, cc, who sent it, etc.

This is a traditional approach:

```Kotlin
class MailBuilder {  
   private var to: List<String> = listOf()  
   private var cc: List<String> = listOf()  
   private var title: String = ""  
   private var message: String = ""  
   private var important: Boolean = false  
  
   class Mail internal constructor(  
      val to: List<String>,  
      val cc: List<String>?,  
      val title: String?,  
      val message: String?,  
      val important: Boolean  
   )  
  
   // For each property, create a similar function to set it  
  
   fun to(to: List<String>): MailBuilder {  
      this.to = to  
      return this  
   }  
  
   fun message(message: String): MailBuilder {  
      this.message = message  
      return this  
   }  
  
   fun build(): Mail {  
      if (to.isEmpty()) {  
         throw RuntimeException("To property is empty!")  
      }  
  
      return Mail(to, cc, title, message, important)  
   }  
}  
  
// Then you can create Mail objects like this:  
  
fun foo(): MailBuilder.Mail {  
   return MailBuilder()  
      .message("message")  
      .to(listOf("rabbit@victor.com"))  
      .build()  
}
```

Create a Builder function that has private mutable properties that are manipulated internally via functions such as `message()` and `to()`. The syntax becomes much clearer.

In Kotlin, however, you don't really need to use the Builder Pattern because there are language features that let you instantiate complex objects using [[data class]] objects and [[Scope Functions]] if needed.

```Kotlin
/*This is what is possible using Kotlin Standard Library,  
 basically removing the need for all the boilerplate*/  
 
// Settings default arguments you are able to skip properties that are not needed during the object creation  
data class Mail_V2(  
   val to: List<String>,  
   val cc: List<String> = listOf(),  
   val title: String = "",  
   val message: String = "",  
   val important: Boolean = false,  
)  
  
// you have named arguments in Kotlin  
val mail = Mail_V2(  
   title = "This is a Title",  
   message = "This is a message body",  
   to = listOf("rabbit@victor.com")  
)
```

