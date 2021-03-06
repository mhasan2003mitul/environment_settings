# Before deploy a jar file in local nexus
You need to modify setting.xml, where 
  <server>
      <id>nexus</id>   // This id would be used as a value of "-DrepositoryId=ID".
      <username>admin</username>
      <password>admin123</password>
    </server>
  </servers>
  
will contain the local nexus login credentials. But you can also use parameter to pass username and password of local nuxus repo.

# Deploy a jar file in local nexus with pom

mvn deploy:deploy-file -DgroupId=nl.rws -DartifactId=rws-project-template -Dversion=1.0 -DgeneratePom=true -Dpackaging=jar -DrepositoryId=nexus -Durl=http://dsonexus.hofcom.org/nexus/content/repositories/archetype/ -Dfile=target/rws-project-template-1.0.jar

# Deploy a jar file in local nexus without pom

mvn deploy:deploy-file -DgroupId=nl.rws.dso -DartifactId=rws-project-template -Dversion=1.0 -DgeneratePom=false -Dpackaging=jar -DrepositoryId=nexus -Durl=http://dsonexus.hofcom.org/nexus/content/repositories/archetype/ -Dfile=target/rws-project-template-1.0.jar

# Install a jar file in local mave repo

mvn install:install-file -Dfile=rws-project-template-1.0.jar -DgroupId=nl.rws.dso -DartifactId=rws-project-template -Dversion=1.0 -Dpackaging=jar

# Generate project from local archetype repositories

mvn archetype:generate -DarchetypeGroupId=ARCHETYPE_GROUP_ID -DarchetypeArtifactId=ARCHETYPE_ARTIFACT_ID -DarchetypeVersion=ARCHETYPE_VERSION -DarchetypeRepository=ARCHETYPE_HOST_WITH_REPOSITORY -DgroupId=NEW_PROJECT_GROUP_ID -DartifactId=NEW_PROJECT_ARTIFACT_ID

example:

mvn archetype:generate -DarchetypeGroupId=nl.rws.dso -DarchetypeArtifactId=rws-project-template -DarchetypeVersion=1.0 -DarchetypeRepository=http://dsonexus.hofcom.org/nexus/content/repositories/archetype/ -DgroupId=nl.test -DartifactId=nl-test

# Passing argument for the plugins during maven release:perform

mvn release:perform -Darguments="-DargumentName=value"


