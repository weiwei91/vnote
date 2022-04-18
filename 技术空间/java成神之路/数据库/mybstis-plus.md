# mybstis-plus
Integer insert(T var1);

BaseMapper 接口

    Integer insertAllColumn(T var1);
    Integer deleteById(Serializable var1);
    Integer deleteByMap(@Param("cm") Map<String, Object> var1);
    Integer delete(@Param("ew") Wrapper<T> var1);
    Integer deleteBatchIds(@Param("coll") Collection<? extends Serializable> var1);
    Integer updateById(@Param("et") T var1);
    Integer updateAllColumnById(@Param("et") T var1);
    Integer update(@Param("et") T var1, @Param("ew") Wrapper<T> var2);
    Integer updateForSet(@Param("setStr") String var1, @Param("ew") Wrapper<T> var2);
    T selectById(Serializable var1);
    List<T> selectBatchIds(@Param("coll") Collection<? extends Serializable> var1);
    List<T> selectByMap(@Param("cm") Map<String, Object> var1);
    T selectOne(@Param("ew") T var1);
    Integer selectCount(@Param("ew") Wrapper<T> var1);
    List<T> selectList(@Param("ew") Wrapper<T> var1);
    List<Map<String, Object>> selectMaps(@Param("ew") Wrapper<T> var1);
    List<Object> selectObjs(@Param("ew") Wrapper<T> var1);
    List<T> selectPage(RowBounds var1, @Param("ew") Wrapper<T> var2);
    List<Map<String, Object>> selectMapsPage(RowBounds var1, @Param("ew") Wrapper<T> var2);
       
IService 接口

    boolean insert(T var1);
    boolean insertAllColumn(T var1);
    boolean insertBatch(List<T> var1);
    boolean insertBatch(List<T> var1, int var2);
    boolean insertOrUpdateBatch(List<T> var1);
    boolean insertOrUpdateBatch(List<T> var1, int var2);
    boolean insertOrUpdateAllColumnBatch(List<T> var1);
    boolean insertOrUpdateAllColumnBatch(List<T> var1, int var2);
    boolean deleteById(Serializable var1);
    boolean deleteByMap(Map<String, Object> var1);
    boolean delete(Wrapper<T> var1);
    boolean deleteBatchIds(Collection<? extends Serializable> var1);
    boolean updateById(T var1);
    boolean updateAllColumnById(T var1);
    boolean update(T var1, Wrapper<T> var2);
    boolean updateForSet(String var1, Wrapper<T> var2);
    boolean updateBatchById(List<T> var1);
    boolean updateBatchById(List<T> var1, int var2);
    boolean updateAllColumnBatchById(List<T> var1);
    boolean updateAllColumnBatchById(List<T> var1, int var2);
    boolean insertOrUpdate(T var1);
    boolean insertOrUpdateAllColumn(T var1);
    T selectById(Serializable var1);
    List<T> selectBatchIds(Collection<? extends Serializable> var1);
    List<T> selectByMap(Map<String, Object> var1);
    T selectOne(Wrapper<T> var1);
    Map<String, Object> selectMap(Wrapper<T> var1);
    Object selectObj(Wrapper<T> var1);
    int selectCount(Wrapper<T> var1);
    List<T> selectList(Wrapper<T> var1);
    Page<T> selectPage(Page<T> var1);
    List<Map<String, Object>> selectMaps(Wrapper<T> var1);
    List<Object> selectObjs(Wrapper<T> var1);
    Page<Map<String, Object>> selectMapsPage(Page var1, Wrapper<T> var2);
    Page<T> selectPage(Page<T> var1, Wrapper<T> var2);