# Create Jar with dependencies



````
task createJar(type: Jar) {
    manifest {
        attributes 'Implementation-Title': 'Demo Projekt',
                   'Implementation-Version': version,
                   'Main-Class': 'com.example.MainFxLauncher'
    }
    
    baseName ='DemoProjekt-full'

    exclude "META-INF/*.SF"
    exclude "META-INF/*.DSA"
    exclude "META-INF/*.RSA"

    from { configurations.compile.collect { it.isDirectory() ? it : zipTree(it) } }
    with jar
}
````
# Run class

````
task executeNespaRedWinLogin(type:JavaExec) {
    main = "com.example.MainFxLauncher"
    classpath = sourceSets.main.runtimeClasspath
    // args '--version'
}
````
