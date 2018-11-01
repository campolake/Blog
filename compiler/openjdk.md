# 一  classFile 的解析

```  C++
juint AltHashing::compute_seed() {
  jlong nanos = os::javaTimeNanos();
  jlong now = os::javaTimeMillis();
  int SEED_MATERIAL[8] = {
            (int) object_hash(SystemDictionary::String_klass()),
            (int) object_hash(SystemDictionary::System_klass()),
            (int) os::random(),  // current thread isn't a java thread
            (int) (((julong)nanos) >> 32),
            (int) nanos,
            (int) (((julong)now) >> 32),
            (int) now,
            (int) (os::javaTimeNanos() >> 2)
  };

```