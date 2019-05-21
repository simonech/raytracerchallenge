# The Ray Tracer Challenge... in .NET Core

This repo holds the code for a ray tracer following this book: [The Ray Tracer Challenge - A Test-Driven Guide to Your First 3D Renderer](http://www.raytracerchallenge.com/).

I'm blogging my adventures implementing this ray tracer on my blog: [codeclimber.net.nz](https://codeclimber.net.nz).

## Technologies used

The project will be implemented with .NET Core 2.2, with no external libraries, to adhere the most to the concept of the book, which is to build everything from scratch, even features that might exist already as part of .NET Standard or in other packages, like `Color`, `Point`, image rendering and serializing.

My objective is also to build everything using a Mac, the `dotnet` CLI and VS Code, to prove (mostly to myself) that this is a feasible approach, and that you can do everything you need without the full-blown Visual Studio.

I'll also try to use the latest features of the C# language, whenever makes sense.

The book recommends the usage of Cucumber for the testing, and even provides the full set of features in Gherkin. SpecFlow is the only Gherkin implementation for .NET, but seems like the support for .NET Core is not very advanced, and still relies on their Visual Studio plugin for generating the test files. So I'll start with plain old unit testing with xUnit, and will move to SpecFlow later.

## What I'm trying to achieve

Nowadays I spend most of my time building CMS-based projects, using APIs provided by vendors, and aggregating results coming from Cloud-based services. So, mostly I want to re-discover the fun of developing something from scratch.

I also want to learn new things, improve the knowledge I have and, since there is a lot math involved, re-learn things I've learned at the university.

Specifically, things I hope to learn better are:

 * Obviously, how raytracing works;
 * Math, Algebra, Matrix, Vectors and similar stuff;
 * usage of the `dotnet` CLI;
 * a more advanced usa of VS Code (now I mostly use it "just" as text editor);
 * New features of C# (with new I mean from v6 onwards);
 * xUnit;
 * BDD with Gherkin and SpecFlow.

## Repository structure

This `master` branch contains the latest state of the ray tracer library and tests. Additionally, some chapters have some self-contained applications, so there will be some additional projects as well.

To look at how the main library and test suite evolved through the book, each chapter has a branch, sometimes multiple when it makes sense. It starts with Chapter 0, which is the preparation of environment.


## Creating the structure

```
dotnet new sln -o ray-tracer-challenge
cd ray-tracer-challenge
dotnet new classlib -o raytracer -n codeclimber.raytracer
dotnet new xunit -o xUnit -n codeclimber.raytracer.xUnit
dotnet sln add **/*.csproj || dotnet sln add raytracer/codeclimber.raytracer.csproj xUnit/codeclimber.raytracer.xUnit.csproj
cd xUnit/
dotnet add reference ../lib/codeclimber.raytracer.csproj 
cd ..
dotnet build
dotnet test
```

