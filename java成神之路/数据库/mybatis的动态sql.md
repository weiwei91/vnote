# mybatis的动态sql
# if
有条件的包含where子句一部分
有两种写法

```
<select id="findUserListByCondition" resultMap="BaseResultMap" >
		select
		<include refid="Base_Column_List" />
		from tbuser where 1=1
		<if test="name!=null">
			and name = #{name}
		</if>
</select>

<select id="findUserListByCondition" resultMap="BaseResultMap" >
		select
		<include refid="Base_Column_List" />
		from tbuser
		<where>
		<if test="name!=null">
			and name = #{name}
		</if>
		</where>
	</select>
```

# choose
有时候只需要选择多个条件中的一个

```
<select id="findUserListByCondition1" resultMap="BaseResultMap" >
		select
		<include refid="Base_Column_List" />
		from tbuser
		<where>
			<choose>
				<when test="name!=null">
					and name = #{name}
				</when>
				<when test="telephone!=null">
					and telephone = #{telephone}
				</when>
				<otherwise>
					and role = 3
				</otherwise>
			</choose>
		</where>
	</select>
```

# trim

```

<where></where> 等同于

<trim prefix="WHERE" prefixOverrides="AND|OR ">
  ... 
</trim>

<update id="updateAuthorIfNecessary">
  update Author
    <set>
      <if test="username != null">username=#{username},</if>
      <if test="password != null">password=#{password},</if>
      <if test="email != null">email=#{email},</if>
      <if test="bio != null">bio=#{bio},</if>
    </set>
  where id=#{id}
</update>  等同于

<trim prefix="SET" suffixOverrides=",">
  ...
</trim>

```

# foreach

动态sql另外一个必要操作就是对集合进行遍历，通常是在构建IN 条件语句的时候

```
<select id="selectPostIn" resultType="domain.blog.Post">
  SELECT *
  FROM POST P
  WHERE ID in
  <foreach item="item" index="index" collection="list"
      open="(" separator="," close=")">
        #{item}
  </foreach>
  
</select>

```

# bind 标签的使用

```
<select id="findUserListByCondition4" resultMap="BaseResultMap" >

		<bind name="pass" value="'%' +password + '%'" />

		select
		<include refid="Base_Column_List" />
		from tbuser
		<where>
		<if test="names!=null">
		and name in
		<foreach item="item" index="index" collection="names" open="(" separator="," close=")">
			#{item}
		</foreach>
		</if>
		<if test="password!=null">
			or password like #{pass}
		</if>
		</where>
	</select>

```

基本上掌握以上的标签可以对很多很复杂的多条件查询了


