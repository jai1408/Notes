## Java defines many built-in annotations. Most are specialized, but 9 are general purpose.

### 4 are imported from java.lang.annotation: 
* @Retention, 
* @Documented,
* @Target,
* @Inherited.

### 5 are included in java.lang
* @Override -- marker annotaion, used for method overriding.
* @Deprecated --marker annotation, used for obsolete declaration.
* @FunctionalInterface --marker annotation, informational, used for functional interface.
* @SafeVarargs --marker annotation, indicates that no unsafe actions related to a varargs parameter occur
* @SuppressWarnings --used for one or more warnings by compiler

### NOTE To java.lang.annotation, JDK 8 adds the @Repeatable and @Native. 
* @Repeatable supports repeatable annotations,
* @Native annotates a field that can be accessed by native code.

# JUnit code snippet
	
```
	@Test
	public void retrieveAllSurveyQuestions() throws Exception {
		HttpEntity entity = new HttpEntity<Question>("Doesn't Matter", headers);
		ResponseEntity<List<Question>> response = restTemplate.exchange(createURLWithPort("/surveys/Survey1/questions"),
				HttpMethod.GET, entity, new ParameterizedTypeReference<List<Question>>() {
				});
		Question sampleQuestion = new Question("Question1", "Largest Country in the World", "Russia",
				Arrays.asList("India", "Russia", "United States", "China"));
		assertTrue(response.getBody().contains(sampleQuestion));
	}
```

```	
	@Test
	public void addQuestion() {
		Question question = new Question("DOESNTMATTER", "Question1", "Russia",
				Arrays.asList("India", "Russia", "United States", "China"));
		HttpEntity entity = new HttpEntity<Question>(question, headers);
		ResponseEntity<String> response = restTemplate.exchange(createURLWithPort("/surveys/Survey1/questions"),
				HttpMethod.POST, entity, String.class);
		String actual = response.getHeaders().get(HttpHeaders.LOCATION).get(0);
		assertTrue(actual.contains("/surveys/Survey1/questions/"));
	}
```