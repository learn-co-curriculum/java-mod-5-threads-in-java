# Threads in Java

## Learning Goals

- Explain what a Thread is in Java.
- Use thread instance methods.

## Introduction

Java supports thread at the JVM level, the language level with special keywords,
and has standard libraries to deal with them. Every Java program runs at least
one thread. This thread is called the `main` thread. Over the years, Java has
introduced higher level abstractions to work with threads but we will start with
the fundamentals to develop a solid intuition.

## Thread Objects

In Java, each thread is an instance of the `java.lang.Thread` class or its
subclass. Threads have a name, identifier (`long`), a priority, and other
properties that can be accessed through the instance methods.

Let’s look at an example which prints out the different properties of the `main`
thread.

```java
public class Main {
    public static void main(String[] args) {
        Thread t = Thread.currentThread();

        System.out.println("Name: " + t.getName());
        System.out.println("ID: " + t.getId());
        System.out.println("Alive: " + t.isAlive());
        System.out.println("Priority: " + t.getPriority());
        System.out.println("Daemon: " + t.isDaemon());

        t.setName("custom-thread");
        System.out.println("New name: " + t.getName());
    }
}
```

```plaintext
Name: main
ID: 1
Alive: true
Priority: 5
Daemon: false
New name: custom-thread
```

We first store the current thread reference in the `t` variable and then call
the various instance methods on the `main` thread instance.

Threads with a higher priority are executed over threads with lower priority.
Daemon threads are low priority threads that can run in the background. The JVM
does not wait for daemon threads before exiting.

## Conclusion

We’ve looked at the common methods for getting information on a thread. Note
that all of these methods can be run on any thread and not just the `main`
thread.
