# BaseAsyncTask Package 

## Motivation 

The Android system prevents tasks such as database access and internet operations from occurring on the main thread (UI Thread), 
as they can generate crashes that harm the user experience. At the same time, the System also does not allow UI component updates
to be made in the Main Thread. With this in mind, it is common to need to perform an asynchronous task in the background whose 
result is used to update the user interface. An example would be consuming a web API to collect product data that will be shown 
to the user. There are some ready-made libraries to deal with this type of situation, such as Kotlin Coroutines and AsyncTask (deprecated). 
<br><br>
That said, this library aims to use a simple and functional implementation to perform this type of task in Android applications. The implementation 
uses the Thread class from Java. 

## Installation

1. Add the JitPack repository to your build file
```
dependencyResolutionManagement {
		repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
		repositories {
			mavenCentral()
			maven { url 'https://jitpack.io' }
		}
	}
```
2. Add the dependency
```
dependencies {
    implementation 'com.github.LucasFerreira9:BaseAsyncTask_Android:Tag'
}
```

## Example of usage 

1. fetching products and updating UI views. 
```
BaseAsyncTask myTask = new BaseAsyncTask(
  ()->{
      // Network operation
      List<products> products = fetchProducts();
      return products;
  },
  (products)->{
      // update UI
      updateProductsViews(products);
  }
);
myTask.run();
```
2. running a simple background task without a result.
```
BaseAsyncTask.runSingleTask(()->{
  //my task here
});
```
