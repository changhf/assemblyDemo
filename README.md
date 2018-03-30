####assembly插件的使用记录
 - pom.xml引入maven-assembly-plugin插件
 - 指定descriptor如src/main/assembly/assembly.xml,或者直接建立一个deploy模块
 指定descriptor如assembly.xml
 - descriptor文件里主要是fileSets和dependencySets
 
     ```
    <dependencySets>
        <dependencySet>
            <outputDirectory>lib</outputDirectory><!-- 将scope为runtime的依赖包打包到lib目录下。 -->
            <scope>runtime</scope>
        </dependencySet>
    </dependencySets>
    ```
     其次是bin和conf的设置
 - 如何引入bin里的脚本呢？project.build.scriptSourceDirectory->maven的目录scripts
    ```
     <fileSet>
         <directory>${project.build.scriptSourceDirectory}</directory>
         <outputDirectory>bin</outputDirectory>
         <filtered>true</filtered>
         <fileMode>0744</fileMode>
         <includes>
             <include>*.sh</include>
         </includes>
     </fileSet>
    ```
