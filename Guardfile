guard :shell do
  watch('pom.xml') do |m|
    title = 'Test'
    eager 'mvn clean && mvn test'
    status = ($?.success? && :success) || :failed
    n '', title, status
    ''
  end

  watch(%r{src/main/java/.+\.java}) do |m|
    title = 'Test'
    eager 'mvn test-compile -q && mvn -Dtest=\`basename #{m[0]} .java\`Test test'
    status = ($?.success? && :success) || :failed
    n '', title, status
    ''
  end

  watch(%r{src/test/java/.+\.java}) do |m|
    title = 'Test'
    eager 'mvn test-compile -q && mvn -Dtest=\`basename #{m[0]} .java\` test'
    status = ($?.success? && :success) || :failed
    n '', title, status
    ''
  end

  watch(%r{src/main/thrift/.+\.thrift}) do |m|
    title = 'Test'
    eager 'mvn generate-sources && mvn test-compile -q && mvn -Dtest=\`basename #{m[0]} .thrift\`Test test'
    status = ($?.success? && :success) || :failed
    n '', title, status
    ''
  end
end
