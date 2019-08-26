# CI FAQ

## Useful DSL

### Print list of plug-ins that are installed
'''
plugins = jenkins.model.Jenkins.instance.getPluginManager().getPlugins().toSorted().each {
println "${it.getShortName()}\t${it.getVersion()}\t${it.getLongName()}";
   out.println "${it.getShortName()}\t${it.getVersion()}\t${it.getLongName()}";
}
println "";
println "Total number of plugins: ${plugins.size()}";
'''

### Print the disk usage
'''
println "\n\n=============== Jobs Using Disk Space ============ \n\n"
println new ProcessBuilder('sh','-c',' du -ah --max-depth=7 /var/jenkins_home/jobs | sort -k 1 -h -r | head -n 1000 ').redirectErrorStream(true).start().text
'''
